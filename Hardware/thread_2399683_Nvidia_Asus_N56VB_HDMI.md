---
title: "Nvidia Asus N56VB HDMI"
date: 2018-08-28
forum: Hardware
---

### Post by jg-jguk on 2018-08-28
Hi there
My Asus N56VB has HDMI output, but I can't figure out how to get it working at 4K with my Ilyama 32inch 4K monitor.

$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)


also:
01:00.0 3D controller: NVIDIA Corporation GK107M [GeForce GT 740M] (rev a1)


Ubuntu Settings did show "Intel Ivybridge Mobile" until I changed to Nvidia driver. But "Screen Display" still only shows 1920x1080

Any tips appreciated!

---

### Post by jg-jguk on 2018-08-29
I rebooted to Windows 10, with Nvidia drivers active, I can't even get it to work there.

Other forum says it's [not possible]("http://techcity.tv/forum/discussion/703/4k-output-over-hdmi-on-laptop")

---

