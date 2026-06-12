---
title: "Can find webcam but can't use it"
date: 2007-10-29
forum: Hardware &amp; Laptops
---

### Post by DalekClock on 2007-10-29
I've got a USB webcam that uses the CiPA chip. It's recognised by my computer as /dev/video0 and Linux has a driver for it.

When I try to use it with Camorama, I get the following error:```
Could not connect to video device (/dev/video0).
Please check connection
```What does this mean?

---

### Post by kast on 2007-10-29
I know this might not be that helpful, and that you probably tried this already, but i have received that message before and i just switched to another USB and restarted my pc. Might have not needed the restart but its a bad habit to break :)

---

### Post by DalekClock on 2007-10-30
I've tried it on all available USB ports my PC has to available, still no luck.

---

### Post by Ubuntwan on 2007-10-30
It looks very much like the problem I have with my webcam (see [http://ubuntuforums.org/showthread.php?t=595924]("http://ubuntuforums.org/showthread.php?t=595924"))
Do you have the same outputs of the commands? Perhaps it is the same (unsolved) problem but with a different camera, which may indicate it is not camera related...

**UPDATE:** *hermz2507* helped me out with my problem with info he found on [http://lists.zerezo.com/spca50x-devs/msg01290.html]("http://lists.zerezo.com/spca50x-devs/msg01290.html") and it worked for my trust wb 1400t webcam. Perhaps that list has an answer to your cams problem as well (if you use that driver also).
good luck

---

