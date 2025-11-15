<!DOCTYPE html>
<html>
<head>
<title>Screen Share Permission</title>
</head>
<body style="text-align:center; font-family:sans-serif;">
<h2>Do you want to share your screen?</h2>

<button onclick="shareScreen()" 
style="padding:10px 20px; font-size:18px;">YES</button>

<button onclick="alert('Screen share canceled')" 
style="padding:10px 20px; font-size:18px;">NO</button>

<script>
async function shareScreen() {
  try {
    const stream = await navigator.mediaDevices.getDisplayMedia({
      video: true,
      audio: false
    });
    
    const video = document.createElement("video");
    video.srcObject = stream;
    video.autoplay = true;
    video.style.width = "100%";
    document.body.innerHTML = "";
    document.body.appendChild(video);

  } catch (e) {
    alert("Screen share blocked");
  }
}
</script>

</body>
</html>
