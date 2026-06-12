---
title: "PI4 crashes with USB3 connected hub."
date: 2019-11-04
forum: Hardware
---

### Post by rewolff on 2019-11-04
I have a Pi4 running Ubuntu. I need the 64-bit kernel. I found a "how to change your pi3 image to run on pi4" tutorial, but it included a link to a ready image and I used that. 

I have 5 USB harddisks doing software raid5. As the pi doesn't have five USB3 ports, I use an USB3 HUB and one direct connection. Each of the five drives has its own 12V powersupply.

The system has been very unstable.... Until two weeks ago, it crashed and when it came back up (after a manual power cycle of the PI), all the harddrives on the USB hub indicated "USB2" (green led) instead of "USB3" (blue led). It ran much more stable for two weeks until it crashed again friday. I rebooted it sunday morning and got a few harddisks back on USB3. (Invalidating my working theory: "the USB3 hub has the USB3 part broken down"). I then fiddled a bit until all four drives on the hub were showing USB3 again. I then restarted the file-transfer and... the system crashed again a few hours later.

The hub is: [https://www.informatique.nl/554422](https://www.informatique.nl/554422)
The disks are housed in: [https://www.informatique.nl/519874](https://www.informatique.nl/519874) (that's a link to the productID that I actually bought).
But I have an earlier version. (my led is somewhere in the middle, the on-of switch is a slide switch and mine have an USB-A connector).

So.... my analysis so far is that it has to do with the hub running in USB3 mode that creates most of the instability, but running 4 disks at USB2 speeds does not fix it completely. (it still crashed after about 2 weeks).

Does anybody recognize some "known bug" in this story? Any suggestions about how to debug this further?


These are the enclosures and the HUB in lsusb:
Bus 002 Device 003: ID 152d:0578 JMicron Technology Corp. / JMicron USA Technology Corp.
Bus 001 Device 003: ID 2109:2813 VIA Labs, Inc.
Bus 001 Device 002: ID 2109:3431 VIA Labs, Inc. Hub

Nothing about uas in the dmesg output. (Squashfs matches). Ah! my devices are already blacklisted for UAS: "Quirks match for vid 152d pid 0578: 1000000"

Linux anticlimax 4.19.73-v8+ #1 SMP PREEMPT Sat Sep 21 18:47:32 MDT 2019 aarch64 aarch64 aarch64 GNU/Linux

---

### Post by CatKiller on 2019-11-04
If it's the 4 GB version that you're using, there's a bug that makes the USB ports not work properly. The workaround is to limit the machine to 3 GB till the bug gets fixed, possibly in time for the next Hardware Enablement Stack refresh.

There are more details on [the Ubuntu blog.](https://ubuntu.com/blog/roadmap-for-official-support-for-the-raspberry-pi-4)

---

### Post by hk42 on 2019-11-04
USB3 can be tricky .
A solution I found is adding USB3 extension cables or changing the length of existing ones.
Clipping ferrites on the cables could be tried too.
HTH

---

### Post by khowe on 2019-11-04
Check the version of eeprom you have. There have been issues reported with USB.

[https://www.raspberrypi.org/documentation/hardware/raspberrypi/booteeprom.md](https://www.raspberrypi.org/documentation/hardware/raspberrypi/booteeprom.md)
[https://www.raspberrypi.org/forums/viewtopic.php?t=250368](https://www.raspberrypi.org/forums/viewtopic.php?t=250368)

---

