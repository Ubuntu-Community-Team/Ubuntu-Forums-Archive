---
title: "Black Screen of Death on HP DV6"
date: 2010-04-19
forum: Hardware
---

### Post by _0R10N on 2010-04-19
I recently installed Karmic on my HP DV6 laptop. On the first reboot the screen went black, and the only choice was a hard reboot. Then, once in a while, I'm working perfectly and suddenly it freezes the system completely. After a hard reboot, it falls into the same thing after a few minutes, for  2 or more times. And then, days and days without any complaint. And then, back again...

I've read that something like this is happening to other guys, but, so far, I didn't find solution.

Thanks in advance!

_0R10N >>

---

### Post by tanpopo_chan on 2011-03-16
I had the same problem and this is how I fixed mine...

I want to start off by saying that I have an HP Pavillion dv6-2145es with an ATI Mobility Radeon HD 4650, ATI M96 Chipset, and an AMD Turion II Dual-Core Mobile M520 and I'm running Ubuntu 10.10 Maverick Meerkat x64.

This route fixed my problem, but keep in mind that freezing and hangs are very difficult to pinpoint. I suggest you read the wiki page on hangs, lockups, and freezes. It helped me figure out what caused my freezing and helped me find a solution.
- [https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting](https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting)
- [https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

-------

First, I disabled the proprietary drivers by going to *System -> Administration -> Additional Divers* and, after, I installed fglrx manually. 
You can find a guide here: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)

-------

Second, I turned off acpi.

[I]1) In a terminal type
```
sudo gedit /boot/grub/grub.cfg
```

2) Find the option GRUB_CMDLINE_LINUX_DEFAULT and add acpi=off. For example, mine is
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
```

3) Reboot.[/I]

-------

Third, I followed this person's suggestion, since he seemed to have the same problem as me.
[http://ubuntuforums.org/showthread.php?p=10567976](http://ubuntuforums.org/showthread.php?p=10567976)

[I]1) Check proper installation of kernel headers with
```
sudo apt-get install linux-headers-$(uname -r)
```

2)Install the fglrx driver
```
sudo apt-get install fglrx
```

3)Select fglrx (auto mode) to use, selection for me was 0
```
sudo update-alternatives --config gl_conf
```

4)Then:
```
sudo ldconfig
```
```
sudo update-initramfs -u
```

config xorg
```
sudo aticonfig --initial
```[/I]

-------

Fourth, and final step, I followed this man's advice since during different tests, I noticed my problem was the vbetool causing problems. [http://ubuntuforums.org/showthread.php?t=1133319](http://ubuntuforums.org/showthread.php?t=1133319)
```
sudo mv /usr/sbin/vbetool /usr/sbin/vbetool.old
```

---

