---
title: "nvidia driver problem"
date: 2009-08-03
forum: Hardware
---

### Post by hellkiller on 2009-08-03
I have laptop with Nvidia GeForce G102M. I tried to install this driver - [http://www.nvidia.com/object/linux_display_amd64_185.18.31.html](http://www.nvidia.com/object/linux_display_amd64_185.18.31.html)

And now my display is devided into 6 parts. Here's a photo:
[IMG]http://img24.imageshack.us/img24/7560/img4378p.jpg[/IMG]

I tried to manually add a resolution to xorg.conf but it doesn't worked. I can't get resolution bigger than 640x480. 

Any ideas how to fix the problem?

---

### Post by steveneddy on 2009-08-03
Sorry I don't have an answer but I wanted to say:

Cool

Well - you might try reinstalling the video driver.

---

### Post by maiker on 2009-10-13
it is solved here: [http://ubuntuforums.org/showthread.php?t=1247196](http://ubuntuforums.org/showthread.php?t=1247196)

add the following line in the device section of xorg.conf
Option "ModeValidation" "NoTotalSizeCheck"

---

### Post by hellkiller on 2009-10-30
Yes, that one worked for me. Thanks :)

---

