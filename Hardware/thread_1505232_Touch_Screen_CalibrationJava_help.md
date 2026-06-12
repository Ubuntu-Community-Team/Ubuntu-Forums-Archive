---
title: "Touch Screen Calibration?/Java help"
date: 2010-06-08
forum: Hardware
---

### Post by Apetrunk on 2010-06-08
I have an HP tx2510us. Somehow the files from Ubuntu 9.10 or whatever it was went missing so I had to reinstall Ubuntu. This time, the newest version (10.04?) came with everything set up for the touch screen, but it's off a little bit and thinks the screen is smaller than it is. Is there any known way of calibrating that? The stylus is fine; it's a little delayed, but it works correctly.

Also, I am trying to play Runescape, a game that uses Java to run. I thought I had installed Java, but it seems to not have worked. Any help with that would be appreciated. Thanks in advance.

---

### Post by Favux on 2010-06-08
Hi Apetrunk,

I thought the coordinates are suppose to be automatic for Lucid, oh well.  The sample TX2500 xorg.conf attached to the bottom of the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") has coordinates.  You can add the stylus/eraser coordinates to the wacom.conf usb snippet as in Section 2 c).

---

