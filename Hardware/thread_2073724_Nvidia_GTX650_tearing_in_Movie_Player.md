---
title: "Nvidia GTX650 tearing in Movie Player"
date: 2012-10-20
forum: Hardware
---

### Post by jonashendrickx on 2012-10-20
I have been trying to get Movie Player to work without tearing. I have been using the proprietary driver since the open source one isn't completely supported yet in 12.04. I haven't used the open-source driver of 12.10 yet since 12.10 is fairly unstable

Anyway is there a way for me to fix the tearing in Ubuntu 12.04 or Linux Mint 13?

Things I tried is installing Gnome, without luck.
Compiz Settings Manager, no difference
Nvidia Control Panel has VSync enabled, check

If anyone knows a solution for me let me know. If you need more information also let me know. Or post your configuration settings if you have solved the problem.

If you ask me whether I used Google to solve this before posting, yes I did ;)

---

### Post by Lucifer666Inferno on 2012-12-01
Here's how i fixed it:

First you must download the NVIDIA proprietary drivers:
[ftp://download.nvidia.com/XFree86/Linux-x86/304.48/](ftp://download.nvidia.com/XFree86/Linux-x86/304.48/)
[ftp://download.nvidia.com/XFree86/Linux-x86_64/304.48/](ftp://download.nvidia.com/XFree86/Linux-x86_64/304.48/)
[ftp://download.nvidia.com/solaris/304.48/](ftp://download.nvidia.com/solaris/304.48/)
[ftp://download.nvidia.com/XFree86/FreeBSD-x86/304.48](ftp://download.nvidia.com/XFree86/FreeBSD-x86/304.48)
[ftp://download.nvidia.com/XFree86/FreeBSD-x86_64/304.48](ftp://download.nvidia.com/XFree86/FreeBSD-x86_64/304.48)

Then stop the X server with "sudo service lightdm stop"

And install the driver as root with "./NVIDIA-Linux-x86-304.48.run"

Reboot your system and you're done.

---

