---
title: "Black screen during boot!"
date: 2009-12-21
forum: Hardware
---

### Post by Loshmi82 on 2009-12-21
I got problems with my new laptop HP compaq 615, i have a lot of problems with installing and running different linux distributions with it. The problems is the black screen that appears when i try to install or boot the OS. The funny thing is it happened with Ubuntu,Kubuntu,OpenSuse and Mint latest versions.
I was able to bypass the installation with enabling "vesa" mode, or something similar, but...after installation, when i reboot, i get black screen 4 out of 5 attempts...Sometimes though, the OS boots like a charm( 20% of the times).
My laptop is brand new, and i would suspect it is broken in some way but i have windows 7 on it, and it works everytime. So i am guessing that this has to be kernel problem ('cause all those distros have exactly the same problem). Maybe it's my ATI 3200 video card...I don't know. I tried all the different things, ask for help in all the different forums, but i still haven't fixed my problem.
Even the rescue boot, don't work out everytime...Live CD cannot boot at all (always black screen after kernel loads). When i delete "quite splash" from the grub...the last thing i get when i try to load OS, is the line containing the "acpi video module...."...and after that i just get a black screen.  Eventualy i manage to get into the system (with a lot of rebooting)...the system then downloaded a new kernel 2.6.31, and new ati prop. drivers...and i was thinking..."this should do it", but nah...still the same...
So i figured, maybe you guys could help me.

Thanks in advance!

---

### Post by a.kyppo on 2010-08-01
i had the same problem. On boot setup press F6 and activate option nolapic. after reboot(when you have installed Ubuntu) go to terminal and execute gedit by typing: sudo gedit /usr/share/grub/default/grub. Edit line 10 to look like this: GRUB_CMDLINE_LINUX="noapic nolapic nodmraid". That helps little bit, but you should install mint 9 as I did. Boots everytime. There are bugs in kernel-version you have on your Live-CD. Ubuntu 10.10 Beta will come in 2.9.2010. That should work. But I recommend to install Mint. It is like Ubuntu but better. Here you can get it [http://www.linuxmint.com/download.php]("http://www.linuxmint.com/download.php")

---

