---
title: "HELP!!! Install Ubuntu 16.10 on ASRock Fatal1ty Z170 machine"
date: 2016-12-05
forum: Hardware
---

### Post by micnguyen2 on 2016-12-05
[FONT=Open Sans, Helvetica, Arial, sans-serif][COLOR=#666666]Hi all,

I tried to install Ubuntu server 16.10 on my machine. Here is the configuration[/COLOR][/FONT]

[LIST]
[*=left]1 x ASRock Fatal1ty Z170 Professional Gaming i7 LGA 1151 Intel Z170 HDMI SATA 6Gb/s USB 3.1 USB 3.0 ATX Intel ...
[*=left]1 x Intel Core i7-6700K Skylake Quad-Core 4.0 GHz LGA 1151 91W BX80662I76700K Desktop Processor Intel HD Graphics ...
[*=left]1 x SAMSUNG 850 EVO 2.5" 1TB SATA III 3-D Vertical Internal Solid State Drive (SSD) MZ-75E1T0B/AM
[*=left]1 x G.SKILL Ripjaws V Series 32GB (2 x 16GB) 288-Pin DDR4 SDRAM DDR4 3200 (PC4 25600) Intel Z170 Platform Desktop ...
[*=left]2 x Nvidia Titan X Pascal
[/LIST]
[LEFT][FONT=inherit]It keeps getting stuck during the installing process with the error of 
[B]ata7.00: failed to IDENTIFY (I/O error, err_mask=0x4)

[/B]I did put these 2 parameters as well:
i915.enable_execlists = 0 and i915.ips =0

I am not sure what to do... I need the computer for Machine Learning purposes.

Thank you for all the help
Mic[/FONT][/LEFT]

---

### Post by karl96 on 2016-12-05
What happens if you boot with ```
pci=nomsi
```?

---

### Post by micnguyen2 on 2016-12-05
Still the same... frozen at the same error.

---

### Post by karl96 on 2016-12-05
Ok, seems to be an issue with the drive from the error message.
Try,
```
acpi=off
```

Otherwise if you could tell me your BIOS settings for hard drives that would help.

If you can get into a shell, dmesg and any logs would be useful to see if any more info can be found.

---

### Post by micnguyen2 on 2016-12-05
I want to attach the error photo here.

[ATTACH=CONFIG]272558[/ATTACH]

This is my BIOS setup

[ATTACH=CONFIG]272559[/ATTACH]

---

### Post by karl96 on 2016-12-05
Do you have an optical drive?
Might seem like a weird request but what happens if you leave your DVD drive open or boot with a disc inserted?

Also what's in slot A7? (the screenshot isn't scrolled down fully)

---

### Post by micnguyen2 on 2016-12-05
Still froze at the same error

I booted with the disk inserted (trying to install the server)

@Karl96: There is no A7. Here is the rest of the setting

[ATTACH=CONFIG]272560[/ATTACH]

---

### Post by karl96 on 2016-12-05
Sorry it is taking so long. The issue looks to be with drive 7? (I think so) So I need to see what's actually on it (just scroll down from BIOS) :)

Otherwise i'm not really sure, there can be so many explanations for these annoying things :(

Edit. We seem to have a habit of posting at the same time and contradicting each other haha.

Edit 2:
Try moving your drive to another SATA port.

---

### Post by oldfred on 2016-12-05
On three different systems (Asus & Gigabyte) I have had issues, by not using ports in order for drives starting at SATA0.
Rebooting with flash drive changed device from sdb to sdc. Having DVD in between two drives made sdb as hd2, not hd1.

And others with older Asrock boards have had issues with Asmedia ports. Even plugging in a DVD drive to ASmedia port caused issues. Only use the first SATA ports that are Intel.

       Some have issues with Asrock and its asmedia ports
UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
[http://www.asrock.com/mb/Intel/Z77%20Pro3/?cat=Manual](http://www.asrock.com/mb/Intel/Z77%20Pro3/?cat=Manual)

The AMD versions also have issues with IOMMU, not sure if also on Intel based versions.

 Asus Sabertooth 990FX: Easy solution to get IOMMU working on mobos with broken BIOSes. 
[http://ubuntuforums.org/showthread.php?t=2254677](http://ubuntuforums.org/showthread.php?t=2254677)
[SOLVED] GPU Passthrough - IOMMU not working for me - on SkyLake 16.04 AsRock
[https://ubuntuforums.org/showthread.php?t=2322179](https://ubuntuforums.org/showthread.php?t=2322179)

---

### Post by micnguyen2 on 2016-12-05
Switching the SATA ports worked! Oh boy... 2 days for no reasons! Thank you @oldfred and karl96. This is very stupid problem!

---

### Post by oldfred on 2016-12-05
Glad that worked.
You can change to [Solved].

---

