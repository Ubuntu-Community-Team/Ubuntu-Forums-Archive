---
title: "Which 1080p @ 60 fps webcam do you recommend for Ubuntu (actually running 60 fps)?"
date: 2020-07-13
forum: Hardware
---

### Post by adam-przedniczek on 2020-07-13
**I've already solved it, Question to be closed/deleted**  [https://askubuntu.com/questions/1258014/solved-making-1080p-webcam-running-at-60-fps-using-uvc-1-5](https://askubuntu.com/questions/1258014/solved-making-1080p-webcam-running-at-60-fps-using-uvc-1-5)

-------------------------------------------

I would like to upgrade my webcam to one offering FHD (1920x1080) resolution at 60 fps (**actually running 60 fps**) that has full support under Ubuntu 20.04 and as far as I know, I should look for a **UVC 1.5** (USB video device class) compliant device.

Preliminary I've pre-selected (,but haven't bought yet) Logitech StreamCam, however I'm a bit worried about the conclusion of the following post: [Logitech Streamcam not offering all modes on Manjaro]("https://superuser.com/questions/1540980/logitech-streamcam-not-offering-all-modes-on-manjaro") (I know that's not Ubuntu, but I think this problem is rather distribution independent).

To make the long story short, on [UVC Wikipedia]("https://en.wikipedia.org/wiki/USB_video_device_class#Operating_system_support") there's stated that Linux **only detects 1.5** devices without providing full capabilities, only trying to fall safe to 1.0 or 1.1 version. Does this statement still hold even in newest kernel? Still we haven't got fully-fledged 1.5 UVC?
However, on [www.ideasonboard.org/uvc/]("https://www.ideasonboard.org/uvc/") I've checked that even in current implementation UVC supports MJPEG (Motion JPEG) and this particular webcam rely on MJPEG payloads.
Meanwhile, I asked for a recommendation on [Quora]("https://www.quora.com/Which-1080p-at-60-fps-webcam-do-you-recommend-for-Linux-e-g-supported-in-Ubuntu-20-04-that-its-actually-running-60-fps") and according to Hans' answer, Logitech C930e (pity that only 30fps) that is UVC 1.5, works perfectly in Ubuntu since 16.04. Now, I'm a little bit confused.

To sum up:

[LIST=1]
[*]**Do you have Logitech StreamCam working at 1080p resolution and running actually 60 fps?** 
[*]**Could you recommend some other 1080p @ 60 fps webcam for Ubuntu 20.04?** 
[*]Does the newest Ubuntu 20.04 (even with kernel lifted to 5.6) has UVC 1.5 support, and if not how to patch it up? 
[*]Does we need the full 1.5 UVC support at all, to have 1080p @ 60 fps or is there any workaround? 
[/LIST]

---

### Post by zebra2 on 2020-07-13
I don't have an idea about your equipment choice but the human mind samples reality at 26 frames per sec. Hence the original fps30 video card.  Movie theater video is 60fps but they show each frame twice with the result of 30fps so far as the video goes, just at a higher resolution.  So what you use in your system should be based on what you want to get.  My son has a masters degree in music and plays in a symphony orchestra so he isn't going to like my sound system. It sounds just fine to me. You should buy what suits your needs and if you have the money then what you need plus what you want. Just my idea on the matter but I don't like paying just for bragging rights.

---

