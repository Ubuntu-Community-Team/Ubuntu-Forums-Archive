---
title: "How to get serial mouse to work?"
date: 2006-11-18
forum: Hardware &amp; Laptops
---

### Post by DoktorNo on 2006-11-18
Hi there,

Is there any chance to get serial (RS-232) mouse to work with Ubuntu? Other Linux distros has no problems with using this kind of hardware. I have Genius NetScroll+ mouse, and Damn Small Linux has seen this mouse as "KYE|0004 scrollmouse" during hardware detection.

---

### Post by viju on 2006-11-20
I have same problem with LIVE CD UBUNTU.It does not work while booting.But It works when I edit /etc/X11/xorg.conf as follows.
Replace "Protocol" "Im PS/2"  with "Protocol" "Microsoft" and "Input device" "/dev/input/mice" with "Input device" "/dev/ttyS0" Save file and restart X. Mouse start working.

---

### Post by DoktorNo on 2006-11-21
It works! Thanks a lot!

But there is a problem: mouse roll doesn't work... Any ideas?

---

