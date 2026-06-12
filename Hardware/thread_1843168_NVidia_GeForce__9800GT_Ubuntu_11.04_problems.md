---
title: "NVidia GeForce  9800GT Ubuntu 11.04 problems"
date: 2011-09-13
forum: Hardware
---

### Post by miroi on 2011-09-13
Hi all,

with Ubuntu 11.04 I got problems with the proprietary nvidia-current driver (GeForce 9800GT), both  280.13 (X updates repository) and 270.41.6 (Ubuntu repository) versions on my amd64 desktop.

During booting the screen gets blank with bright-violet color and it takes very log to start X-server. Sometimes I have to interrupt and run through recovery mode.

The nvidia-bug-report.sh report is attached (generated when I finally get X-server running); I stress these lines containing error message:


[   831.404] (WW) xf86CloseConsole: KDSETMODE failed: Input/output error
[   831.404] (WW) xf86CloseConsole: VT_GETMODE failed: Input/output error
[   831.404] (WW) xf86OpenConsole: VT_GETSTATE failed: Input/output error
[   831.404]
Fatal server error:
[   831.404] xf86CloseConsole: VT_ACTIVATE failed: Input/output error


Any help please ?

PS: The same card worked well with older ubuntu 10.04 and nvidia-173 driver; problems got after upgrade to 11.04.

---

### Post by miroi on 2011-09-17
Well,
blank screen during boot was issue of grub; see:

[http://ubuntuforums.org/showpost.php?p=11258868&postcount=538](http://ubuntuforums.org/showpost.php?p=11258868&postcount=538)

---

### Post by maul9999 on 2011-09-17
Do you activates your video card by hardware device?  Are you sure that you find right bit? (32 or 64).  What bit do you choose before you install ubuntu?

---

