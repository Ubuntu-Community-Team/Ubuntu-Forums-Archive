---
title: "Problem with 4k display and NVIDIA Optimus"
date: 2016-03-07
forum: Hardware
---

### Post by leonardo30 on 2016-03-07
Hello everyone!

I recently bought an ASUS K501UX (FI115T model), and installed Ubuntu GNOME 15.10 on it, in dual boot with Windows 10.
My notebook has a NVIDIA GeForce GTX 950M graphic card (with Optimus) and a 4k display. After the installation I encountered some problems with nouveau, but I finally managed to install bumblebee, namely I simply followed the wiki [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee) and executed from terminal ```
[COLOR=#333333]sudo apt-get install bumblebee bumblebee-nvidia primus linux-headers-generic[/COLOR]
``` and rebooted. After that, things started working properly (in fact before that xrandr always gave me the error "[COLOR=#111111][FONT=Consolas]Failed to get size of gamma for output default[/FONT][/COLOR]", but after that it doesn't any more), but not completely.
In fact, if for example I try to run glxgears with optirun I get the following error:
```
$ optirun glxgears[ 2349.486676] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver


[ 2349.486719] [ERROR]Aborting because fallback start is disabled.
```

Furthermore, there are some programs which are not correctly visualized, in particular text and icons are much smaller than usual (but I don't know if this is related to my problem or if it's simply due to the programs themselves, or simply to the high resolution). For example:
[ATTACH=CONFIG]267694[/ATTACH][ATTACH=CONFIG]267696[/ATTACH][ATTACH=CONFIG]267695[/ATTACH][ATTACH=CONFIG]267697[/ATTACH][ATTACH=CONFIG]267698[/ATTACH]


So my question is: why does optirun says that even if I have installed the driver?
Can anybody help me?

Thanks a lot

If it can be of any help:
```
$ lspci
00:00.0 Host bridge: Intel Corporation Sky Lake Host Bridge/DRAM Registers (rev 08)
00:02.0 VGA compatible controller: Intel Corporation Sky Lake Integrated Graphics (rev 07)
00:04.0 Signal processing controller: Intel Corporation Device 1903 (rev 08)
00:14.0 USB controller: Intel Corporation Device 9d2f (rev 21)
00:14.2 Signal processing controller: Intel Corporation Device 9d31 (rev 21)
00:15.0 Signal processing controller: Intel Corporation Device 9d60 (rev 21)
00:15.1 Signal processing controller: Intel Corporation Device 9d61 (rev 21)
00:16.0 Communication controller: Intel Corporation Device 9d3a (rev 21)
00:17.0 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Device 9d10 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Device 9d14 (rev f1)
00:1c.5 PCI bridge: Intel Corporation Device 9d15 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Device 9d48 (rev 21)
00:1f.2 Memory controller: Intel Corporation Device 9d21 (rev 21)
00:1f.3 Audio device: Intel Corporation Device 9d70 (rev 21)
00:1f.4 SMBus: Intel Corporation Device 9d23 (rev 21)
01:00.0 3D controller: NVIDIA Corporation GM107M [GeForce GTX 950M] (rev a2)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
03:00.0 Network controller: Intel Corporation Wireless 7265 (rev 59)
```

---

### Post by oldfred on 2016-03-07
Do not know dual video, but saw this. What kernel are you using?

       Have Troubles With 4K Displays On Intel Linux? Try The Linux 4.3 Kernel
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4K-4.3-Fix](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4K-4.3-Fix)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2015-11-30-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2015-11-30-wily/)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
[http://blog.ffwll.ch/2015/09/neat-drmi915-stuff-for-43.html](http://blog.ffwll.ch/2015/09/neat-drmi915-stuff-for-43.html)

---

### Post by leonardo30 on 2016-03-07
I'm actually using 4.3.3:
```
$ uname -r
4.3.3-040303-generic
```

---

### Post by leonardo30 on 2016-03-09
Does anybody know what can I do in order to make things work?

---

