---
title: "webcam works with skype but not with cheese"
date: 2011-06-14
forum: Hardware
---

### Post by JorgeM93 on 2011-06-14
Hi folks

 I have just bought a generic web cam ("star tec ST-HC-328" ) and I have the following problem:
 The camera works OK with skype, and "v4l2ucp" detects it fine: it shows me the video previews and says it works with the driver "uvcvideo".
 However, neither cheese nor camorama detect the webcam. Camorama throws a "could not connect to video device (/dev/video0)" error, and cheese crashes while starting (launching it with the terminal shows "segmentation fault" or something like that).
 What it is more strange to me is that "Camera monitor" indicates that the camera is connected ONLY when I start "v4l2ucp" or skype's video preferences.

Any idea about this issue? Does anybody have the same problem? I would appreciate any help.

Thanks

---

### Post by JorgeM93 on 2011-06-16
After digging a lot in google I finally found how this webcam works.

The device's ID, according to lsusb, is 1c4f:3002 SiGma Micro (many cheap cameras use this same product ID). The camera happens to be UVC compilant, that's why it is "plug and play".

These cams don't work with cheese nor camorama, but you can still take photos and record videos using a UVC-based program like Guvcview. Kamoso also detects it well (but I personally prefer Guvcview though). Like I said before, videochat is possible through skype and also with ekiga, which is good, but emesene doesn't seem to detect it, I haven't tested empathy yet.

There's a link [here]("http://www.mail-archive.com/linux-uvc-devel@lists.berlios.de/msg02899.html") of a mailing list where some guys purpose a patch to solve some of the problems; however, it seems to be a bit hack-ish and sincerely I think that the camera works: its own way but it works.

I hope this can help other users who have these type of webcams.

---

