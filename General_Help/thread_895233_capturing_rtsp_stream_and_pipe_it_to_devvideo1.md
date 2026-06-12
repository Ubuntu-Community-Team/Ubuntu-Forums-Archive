---
title: "capturing rtsp stream and pipe it to /dev/video1"
date: 2008-08-20
forum: General Help
---

### Post by harty83 on 2008-08-20
Okay, I'm trying to capture a rtsp stream from a gadspot gsn1250 ip camera and pipe it to /dev/videoX

I am using openRTSP, ffmpeg, vpipe, and vloopback to attempt to accomplish this.  

I have the latest version of ffmpeg from SVN installed.  I have vpipe and vloopback installed.  I have vloopback and videodev modules loaded.

Now, when I run:

```
openRTSP -c -t -v rtsp://myserver:554/video.mp4 | ffmpeg -f mjpeg -i - -f rawvideo -pix_fmt rgb24 - | vipe-f rgb -i 0
```

I connect to the ip camera but at the end, ffmpeg spits out
```
[mjpeg @ 0xd644b0]Could not find codec parameters (Video: mjpeg)
pipe:: could not find codec parameters
```

Any ideas on what is causing this?

---

### Post by harty83 on 2008-08-20
Just a clarification.  The video is obviously not working because ffmpeg is having some codec issue as indicated above.

Thanks,
Alan

---

