---
title: "Camera works in Ubuntu, not Kubuntu"
date: 2020-05-08
forum: Hardware
---

### Post by pseudotheist2 on 2020-05-08
So, with the LTS releases out, i've been playing with both Ubuntu & Kubuntu Fossa...

I was surprised to discover that the webcam does not work on Kubuntu.  I do have  /dev/video0 & /dev/video1, as well as a selectable "USB 2.0 camera, blah..." in the video app, but I get no video feed.
I came back to Gnome Ubuntu to verify, and yep, the video comes right up in the same browser & app.  I'm probably ignorant here, but I assumed the hardware would be handled by the kernel (and further assume that Ubuntu 20.04 & Kubuntu 20.04 use the same kernel).  But it would seem that there's some aspect of the "desktop" that's preventing the hardware from communicating with the app.
Am I making a bad assumption somewhere?  Can anyone who knows a bit more about the differences between an Ubuntu & Kubuntu load point me toward the possible missing link?

---

### Post by pseudotheist2 on 2020-05-28
found the problem by following a link in [another thread]("https://ubuntuforums.org/showthread.php?t=2444221"): [https://dmaiorino.com/?p=12](https://dmaiorino.com/?p=12)
Apparently the default user was created without the video group association.
Much thanks to [DuckHook]("https://ubuntuforums.org/member.php?u=1256508") for the link!

---

