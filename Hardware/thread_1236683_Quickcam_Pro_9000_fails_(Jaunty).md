---
title: "Quickcam Pro 9000 fails (Jaunty)"
date: 2009-08-10
forum: Hardware
---

### Post by nk711 on 2009-08-10
Hi, this webcam works for a while, then fails. I can reliably make it fail by turning 'local video' off then on a few times in Ekiga. It gives the error:

```
libv4l2: error setting pixformat: Input/output error

```

I get a similar v4l2 error like "can't set pixel format" in Qutecom with same fail.

After it's failed, it won't work any more. For example, luvcview then fails with:
```
Stream settings:
  Frame format: MJPG
Unable to set format: Input/output error
 Init v4L2 failed !! exit fatal
```

Only unplugging and plugging the webcam (or removing and inserting the uvcvideo module) fixes it.

I have the latest hardware version ("0009") of this camera, which is supposed to work with the uvcvideo driver.
I am using 2.6.28-14-generic. I've tried this on both 64-bit and 32-bit systems with the same result. I even tried the latest kernel from kernel.org (2.6.30.4) with the same result.

I'd really appreciate any help, including further tips on troubleshooting. 

Thanks.

---

