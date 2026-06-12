---
title: "Problem with SD-Card reader under ubuntu 16.10"
date: 2017-03-02
forum: Hardware
---

### Post by dandressen on 2017-03-02
Hi,

I am currently running Ubuntu 16.10 GNOME on a thinkpad yoga 460.
So far I've got pretty much everything to work, 
including my integrated LTE-Modem (Seirra Wireless EM 7455), 
which is working great under Kernel 4.8.0-40-generic.

Touchscreen and Wacom pen input are also working.

Only thing I am having trouble with right now is my integrated SD-Card reader.
I cannot get it to work. 

So far I've tried the following things:

Downgrading to Kernel 4.4.0-56-generic 
(worked previously under ElementaryOS, which I had to remove from my machine due to them not allowing people to install software from outside their repos)

Anyways, this did not help and caused trouble with my LTE-Modem.

I also tried installing exfat-fuse and exfat-utils (since the SD-Card is formatted in exfat)
Did not help either.

lspci gives me the following: 

dan@dan-ThinkPad-Yoga-460:~$ lspci
00:00.0 Host bridge: Intel Corporation Skylake Host Bridge/DRAM Registers (rev 08)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 520 (rev 07)
00:08.0 System peripheral: Intel Corporation Skylake Gaussian Mixture Model
00:13.0 Non-VGA unclassified device: Intel Corporation Device 9d35 (rev 21)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Device 9d13 (rev f1)
00:1c.5 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #6 (rev f1)
00:1d.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #9 (rev f1)
00:1e.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO UART Controller #0 (rev 21)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-LP LPC Controller (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection I219-LM (rev 21)
**02:00.0 SD Host controller: O2 Micro, Inc. SD/MMC Card Reader Controller (rev 01)**
03:00.0 Network controller: Intel Corporation Wireless 8260 (rev 3a)
06:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 940M] (rev a2)


I assume it is some kernel issue like it was under elementary. 
Can anyone confirm and more importantly, is there a fix for this?

Thanks in advance.

Dan

---

### Post by cariboo on 2017-03-02
Open a terminal and type:

```
dmesg
```

you should see something similar to with, plus error mesages if any.

```
mmc0: new SD card at address b368
[  789.105187] mmcblk0: mmc0:b368 SMI   244 MiB 
[  789.107240]  mmcblk0: p1
```

**Note:** I'm running 17.04 so you may not quite see the same message.

---

### Post by dandressen on 2017-03-02
dsmeg gives me some huge output with some error messages. 

One that appears multiple times is this:

   **[    2.919618] mmc0: tuning execution failed: -5**
 [B][    2.919622] mmc0: error -5 whilst initialising SD card
[/B]
and this as well:[B]

   **SDHCI controller found [1217:8520] (rev 1)**
 **[    2.520614] mmc0: Unknown controller version (3). You may experience problems.**



[/B]Sorry I cannot post the entire output due to forum restrictions.

But I think the problem must be related to one of these.

Is there a fix for that?

---

