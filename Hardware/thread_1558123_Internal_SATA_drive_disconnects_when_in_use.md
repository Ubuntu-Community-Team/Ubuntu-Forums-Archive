---
title: "Internal SATA drive disconnects when in use"
date: 2010-08-21
forum: Hardware
---

### Post by Maloric on 2010-08-21
I've scoured the internet searching for an answer to this one, with no luck.

I've just installed Lucid Lynx on an old PC with a 360GB IDE Hard Drive.  I have a 2TB External SATA Drive, which I then took out of its case and installed into the PC to make it an internal drive.  The drive is brand new and works fine, except that it came formatted as FAT32 (something I didn't realise right away).

Now then, I managed to get Ubuntu up and running without too much difficulty, and installed XBMC.  However I noticed that when using XBMC that my SATA drive would disconnect periodically, and I would have to remount it.  I switched off the feature that automatically generates thumbnails for videos and it stopped happening - great!

But then I decided to reformat the drive to NTFS so I could have HD movies on there.  I started backing up my files, only to find that the drive would disconnect whilst transferring files, in the same way that it did in XBMC.  I tried putting it back into the enclosure and connecting it via USB, and it works fine.  I also tried connecting the drive to another PC running windows 7 and it also works flawlessly.

This leads me to believe that there is something wrong with the SATA controller on my motherboard, as the IDE drive works fine.  I decided to try and find up to date drivers for my motherboard or SATA controller, but that's proved nigh on impossible.

My motherboard is a GA-T671MG - I can't see a manufacturer's name on the board but it was in a prebuilt Packard Bell PC.  The southbridge chip is a SiS968, for which there are only Vista drivers on the SiS website.  The northbridge chip is a SiS671, though I'm assuming that doesn't matter (sorry - I'm a bit inexperienced with this kind of technical hardware stuff).

I checked /var/log/messages and this line appears quite frequently:

```
Aug 21 20:32:13 media kernel: [  106.004060] ata3: soft resetting link
```I don't know if that is significant or not, but am wondering if there a better way to determine why my hard drive is disconnecting? Or if there are any appropriate drivers out there that anyone knows of?  I'm reluctant to spend money on a new motherboard, SATA/IDE converter or use the drive externally, though they look like my only options at the minute.

Here is the output of lspci in case this is helpful:

```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7900 GS] (rev a1)

```

---

### Post by Yellow Pasque on 2010-08-21
What model is your system? Look for a BIOS update...

---

### Post by Maloric on 2010-08-22
I found a sticker on the back of the case that I can't believe I missed until now, telling me that it was a Packard Bell iMedia J2422.  So I went to the Packard Bell website, which has no such system listed in the support section.  I went through all of the iMedia models there anyway to check and none had SiS chipsets, so I'm pretty sure they're not there.

In the legacy downloads I did find Vista drivers, but nothing for Linux and no BIOS.

In addition to this, my BIOS is Pheonix Award, Version Si671V18 (06/03/2008).

I'm at a loss - perhaps the motherboard is faulty and I'll just have to shell out for a new one, though any help diagnosing the issue would still be appreciated.

---

### Post by asasoft on 2010-08-22
Change the sata cable, also check system / administration / Disk utility / Smart Data , and look there for UDMA crc error rate.

---

