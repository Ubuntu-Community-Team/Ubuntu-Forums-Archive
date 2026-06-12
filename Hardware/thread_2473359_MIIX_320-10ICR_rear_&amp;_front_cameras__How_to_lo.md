---
title: "MIIX 320-10ICR rear &amp; front cameras | How to load kernel drivers ov2680 and ov5670 ?"
date: 2022-04-01
forum: Hardware
---

### Post by nico-suricata on 2022-04-01
Hello,

First of all thank you Ubuntu/Debian/Linux community to allow me to use a Linux system and upgrade myself since almost 10 years now. 

Some people try to use Lenovo MIIX 320-10ICR rear and front cameras, which are ov2680 and ov5670 Camera ISP Driver, which would use an &#8220;Intel Image Signal Processor&#8221;. But the kernel which has the driver specifications, seems to do not load it for Ubuntu 18.04/20.04/22.04.

Thank you to "dieter-erich" who had already posted in the forum this question without solutions : 
howto compile cam drivers MIIX 320 ?
[https://ubuntuforums.org/showthread.php?t=2415014](https://ubuntuforums.org/showthread.php?t=2415014)

An investigation was done with lspci and lsusb "terminal query commands" : 
[https://ubuntu-mate.community/t/audio-and-cameras-not-working-on-lenovo-miix-320-10icr/21406](https://ubuntu-mate.community/t/audio-and-cameras-not-working-on-lenovo-miix-320-10icr/21406)

Unless if I mistaken, maybe an interesting analyze come from shootmeshamrock.com :
[https://shootmeshamrock.com/blogs/tech/arch-linux-on-lenovo-ideapad-miix-320](https://shootmeshamrock.com/blogs/tech/arch-linux-on-lenovo-ideapad-miix-320)
"Anyway, the sleep mode not working had me vexed. Luckily the soon-to-be-released kernel version 4.20 will address it. It turns out the Miix 320 has a chip called the Intel Signal Processor to control the cameras. A driver for this chip was supplied in kernel versions 4.12 &#8211; 4.17 but then removed as it allegedly did not work very well. Without the driver, the chip would not get disabled at bootup and then prevent the system from entering S3 sleep."

Thank you to "olek" who talked about the transistion between ubuntu 18.04 and ubuntu 20.04:
[https://ubuntu-mate.community/t/ubuntu-mate-on-a-hybrid-lenovo-miix-320/22042/5](https://ubuntu-mate.community/t/ubuntu-mate-on-a-hybrid-lenovo-miix-320/22042/5)

But it&#8217;s not clear, and we don&#8217;t know if the cameras work for Ubuntu 18.04 ? I guess no, because after boot on the live USB &#8220;Ubuntu 18.04 LTS Linux 4.15&#8221; the &#8220;Cheese&#8221; program continue to refuse to load the camera &#8220;no device found&#8221;. 

About the need : 
The system will been designed for "motion" in a closed circuit without internet, so no kernel upgrade. 

Questions : 
Is it possible to load cameras driver in kernel and recognize cameras ?
Is it necessary to compile drivers and load them at the kernel boot ? If yes how to compile drivers or how to allow them to recognise cameras devices ?
Is it possible to patch the kernel ?

Finally, how to use MIIX 320-10ICR cameras on Ubuntu or Debian, Arch, Suse, Fedora&#8230; ? Maybe the solution is simple ?

Thank you for your time

Nicolas


Sources : 
Drivers :
[https://cateee.net/lkddb/web-lkddb/VIDEO_OV5670.html](https://cateee.net/lkddb/web-lkddb/VIDEO_OV5670.html)
[https://cateee.net/lkddb/web-lkddb/VIDEO_OV2680.html](https://cateee.net/lkddb/web-lkddb/VIDEO_OV2680.html)
[https://github.com/torvalds/linux/blob/master/drivers/media/i2c/ov5670.c](https://github.com/torvalds/linux/blob/master/drivers/media/i2c/ov5670.c)
[https://github.com/torvalds/linux/blob/master/drivers/media/i2c/ov2680.c](https://github.com/torvalds/linux/blob/master/drivers/media/i2c/ov2680.c)
[https://github.com/torvalds/linux/blob/master/drivers/media/i2c/Kconfig](https://github.com/torvalds/linux/blob/master/drivers/media/i2c/Kconfig)

Compile a driver
[https://quick-adviser.com/how-do-i-compile-a-linux-driver/](https://quick-adviser.com/how-do-i-compile-a-linux-driver/)
[https://unix.stackexchange.com/questions/222468/how-to-compile-a-third-party-driver-into-the-kernel](https://unix.stackexchange.com/questions/222468/how-to-compile-a-third-party-driver-into-the-kernel)

Linux kernel : 
[https://soft.lafibre.info/](https://soft.lafibre.info/)

Patch file .c :
[https://www.cyberciti.biz/faq/appy-patch-file-using-patch-command/](https://www.cyberciti.biz/faq/appy-patch-file-using-patch-command/)

Other post : 
[https://esc.sh/blog/linux-on-lenovo-miix-320/](https://esc.sh/blog/linux-on-lenovo-miix-320/)
[https://ubuntu-mate.community/t/audio-and-cameras-not-working-on-lenovo-miix-320-10icr/21406](https://ubuntu-mate.community/t/audio-and-cameras-not-working-on-lenovo-miix-320-10icr/21406)

Miix 320 debian installation :
[https://wiki.debian.org/InstallingDebianOn/Lenovo/MIIX%20320/buster](https://wiki.debian.org/InstallingDebianOn/Lenovo/MIIX%20320/buster)

---

