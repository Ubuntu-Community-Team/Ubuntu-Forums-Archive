---
title: "Dual monitor issue on HP Elite 7500"
date: 2013-10-11
forum: Hardware
---

### Post by misiek2 on 2013-10-11
Hi!

I got new PC at work. It's HP Elite 7500. It came with core i7 3770 and no additional graphics card. So I run on HD4000. This PC has 2 DVI ports to support 2 monitors. One is DVI-I, second one is DVI-D. Monitor connected to DVI-I is working fine. Monitor connected to DVI-D is not detected by system.
My problem is that I cannot get second monitor to work. I have installed Intel drivers (xserver-xorg-video-intel 2:2.21.9-0ubuntu0~raring) but that did not help. Arandr detects only one monitor.
I have checked monitor is actually working - it is.
Checked converter (I am using a converter DVI-D to VGA) - it's OK.

I don't know what to do more. I've been looking all over the Internet, without any success, though.

I have attached some log files, like lspci output. It would so great if you were able to help me with this issue.

Best regards

[ATTACH]246874[/ATTACH]
[ATTACH]246875[/ATTACH]

---

### Post by misiek2 on 2013-10-14
Nevermind, guys. I've finally was able to find the cause of my problem.
It was the way how monitor was connected to the PC. I used a VGA cable with a VGA-DVI-D converter. While DVI-I + VGA cable is working fine, the second configuration not. Don't know if this is converter fault, but when I got a proper double DVI-D cable everything started to work out.
Issue solved.

Best regards

---

