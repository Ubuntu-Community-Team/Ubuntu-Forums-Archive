---
title: "AHCI support on a T61"
date: 2008-03-27
forum: Hardware &amp; Laptops
---

### Post by BrentC on 2008-03-27
Ok, so after reading numerous threads about this topic, I still have NOT found any solution or reasoning for this problem whatsoever.

The problem is that after installing Ubuntu 7.10 in "Compatibility" mode and switching back to AHCI afterwards, I freeze at the Ubuntu Usplash screen. If I switch back to Compatibility, it works fine. What gives?

I read that AHCI was supported in the 2.6 kernel and I am running 2.6.22 at the moment so I'm not sure what the problem is. Does anyone have any ideas on a work around to get AHCI working? If not, does anyone have any idea why this might be happening?

Thanks, Brent.

---

### Post by Whiffle on 2008-03-27
Seems to be a kernel issue.  This might be of some help:
[http://de.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T61#My_DVD_drive.2FCD_burner.2FDVD_burner_doesn.27t_work_.28Solved.29](http://de.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T61#My_DVD_drive.2FCD_burner.2FDVD_burner_doesn.27t_work_.28Solved.29)

Any questions just ask.

---

### Post by BrentC on 2008-03-27
Wow, that was an easy fix! Thanks a lot for the link. I am now one officially happy camper. :)

Still can't believe I never found that link in the 15+ google searches I ran.

Thanks again,
Brent

---

### Post by Whiffle on 2008-03-27
Thinkwiki is fun like that :)  Its the first thing i search when thinkpads are involved.

---

### Post by BrentC on 2008-03-28
Uh oh! It worked the first time then upon reboot, the original problem started happening again. Not sure what went wrong. Only thing I changed was some GUI stuff on Ubuntu, not sure how that would effect AHCI support. :confused:

---

### Post by Whiffle on 2008-03-28
Hmm,  thats strange.  Lets check if the libata module is getting loaded with the atapi_enabled option (i think this should tell us)
```

cat /sys/module/libata/parameters/atapi_enabled

```

thats all i can come up with at the moment...

---

### Post by BrentC on 2008-03-28
The response was a 1, so I assume it is.

---

### Post by Whiffle on 2008-03-28
Next time you boot it, hit "e" at the grub prompt, remove the "silent" and "splash" kernel parameters from the grub line, and then boot it like that.  Hopefully that will let us know where its stopping.

---

### Post by BrentC on 2008-03-28
That's the strangest thing ever. It boots right up when I take out the Usplash, heh. So I guess apparently it WAS in fact the Usplash I added. That is pretty weird if I do say so myself. I can live without a Usplash, but I'm still curious why Ubuntu's Usplash would work and my Mac4Lin Usplash won't. Anyways, thanks again for the help!

EDIT: I spoke too soon apparently, it's slowing down tremendously at the following lines:

> usbcore: registered new interface driver usbhid
/build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: HID core driver
ata1.00: qc timeout (cmd 0xec)
ata1.00: failed to IDENTIFY (I/0 error, err_mask=0x4)
ata1: port is slow to respond, please be patient (Status 0x08)
ata1: COMREST failed (errno=-16)
ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
ata1.00: qc timeout (cmd 0xec)
ata1.00: failed to IDENTIFY (I/0 error, err_mask=0x4)
ata1.00: limiting speed to UDMA7:PIO5
ata1: port is slow to respond, please be patient (Status 0x08)
ata1: COMREST failed (errno=-16)
ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
ata1.00: qc timeout (cmd 0xec)
ata1.00: failed to IDENTIFY (I/0 error, err_mask=0x4)
ata1.00: limiting speed to UDMA7:PIO5
ata1: port is slow to respond, please be patient (Status 0x08)
ata1: COMREST failed (errno=-16)
ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
ACPI: PCI Interrupt 000:00:1f:1[C] -> GSI 16 (level, low) -> IRQ 20

scsi1: ata_piix
scsi2: ata_piix
ata2: PATA max UDMA/100 cmd 0x000101f0 ct1 0x000103f6 bdma 0x00011c00 irq14
ata3: PATA max UDMA/100 cmd 0x00010170 ct1 0x00010376 bdma 0x00011c08 irq15
ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-U10N, 1.05, max UDMA/33
ata2.00: configured for UDMA/33
scs1:0:0:0: CD-ROM             HL-DT-ST DVDRAM GSA-U10N 1.05 PQ: 0 ANSI: 5
Uniform CD-ROM driver Revision: 3.20
sr 1:0:0:0: Attached scsi generic sg0 type 5
Done.

                              Check root= bootarg cat /rpoc/cmdline
                              or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/46b11cab-*insert bunch of numbers that probably mean nothing here* does not exist. Dropping to a shell!

After all of that, it brings me to the BusyBox v1.1.3 ash shell. :( It's strange, it's worked 2 times now the first time around. Then upon reboot, AHCI is like "I'M TAKING THE WHOLE SYSTEM DOWN WITH ME THIS TIME :lolflag:."

---

### Post by BrentC on 2008-03-28
I am happy to announce I have found a solution. I'm not sure whether this will work on the 32-bit side or not, but after having all of these problems, I decided to install the 64-bit version of 7.10 since I have always wanted to try it out and test the compatibility issues with my own T61. After installing and booting in using compatibility mode, I did the automatic updates and what have you. This promptly caused my resolution to be stuck at 600x480. After some reading, I determined a reconfiguration of x-server would solve the problem most likely, but I figured I would just update the kernel to 2.6.24-12-generic just to see if a kernel update could possibly help my AHCI problem also.

I upgraded using the automatic updates, rebooted. After rebooting I found myself stuck at 600x480 resolution. I am assuming rconfiguring x-server would have fixed the problem, but I updated my kernels just because I wanted to see if AHCI would work out of the box on them(Skip to reconfiguring x-server if you don't want to update your kernels). I then installed the following kernel updates:
```
sudo apt-get install linux-restricted-modules-2.6.24-12-generic linux-image-2.6.24-12-generic linux-ubuntu-modules-2.6.24-12-generic
```
Rebooted.

Upon reboot, I reconfigured x-server:
```
sudo dpkg-reconfigure xserver-xorg
```
Rebooted and turned AHCI back on in the BIOs (Config -> Serial ATA -> AHCI)

Upon reaching the GRUB screen, I crossed my fingers and loaded the 2.6.24-12 kernel and voila, I have not had a problem with AHCI since. As I said, this may not be a proper solution for 32-bit versions of Ubuntu, but this is working very nicely in the 64-bit version with full DVD-ROM support. As always, I am not responsible for anything that goes wrong. I am just repeating steps that worked for me in hopes it might possibly help someone else out there.

Also, for anyone interested, I have not had any compatibility issues with the T61 on the 64-bit version of Ubuntu thus far. My specs are as follows:

T61 14.1" WXGA+
T7500 2.2ghz Core 2 Duo
X3100 Intel GMA w/ GM965 chipset
2gb of RAM (Plan on upgrading this to 4gb if I don't find any compatibility issues with the 64-bit. So far I am very pleased with it)
100gb 7200rpm HDD
Slim 8x DVD-ROM Dual Layer writer
Intel Wireless WiFi Link 4965 AGN

---

### Post by SadaraX on 2008-03-31
BrentC, I am glad to hear you are not having anymore hardware problems. I have been running with 7.10 since it came out and I have had only a few small problems so far with my entire experience.

I am interested to know what resolution your monitor is running at and what refresh you are getting? If possible, you could tell me what the results of the command 'xvidtune' tells you? No tweaking required, I am just curious since I find that program is usually more accurate that the Gnome/KDE programs are with their information.

I have had some problems with my video, namely it claims to running at about 60 Hz in KDE's Monitor interface, but 'xvidtune' reports around 48 Hz, and I tend to believe the latter since it actually looks that way...

I am just going to wait until the next version of Ubuntu/Kubuntu comes out and use that, since this is not crucial for me. But if that does not solve me hardware problems I will try your kernel update method.

---

### Post by BrentC on 2008-03-31
I'm running at a resolution of 1440x900. The program xvidtune is showing a vertical sync rate of 59.99 Hz and a horizantal sync rate at 55.56 kHz. Hope this information helps. :)

---

### Post by SadaraX on 2008-03-31
> **BrentC said:**
> I'm running at a resolution of 1440x900. The program xvidtune is showing a vertical sync rate of 59.99 Hz and a horizantal sync rate at 55.56 kHz. Hope this information helps. :)

Hmm, I am running at 1280x800 @ 48 kHz. I cannot raise my resolution or refresh rate. Thanks, for the information.

I am quite pleased the size of 1280x800 but I would like to bump up the refresh rate because I think I can notice some lag when I watch video.

---

