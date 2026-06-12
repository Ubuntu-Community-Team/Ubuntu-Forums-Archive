---
title: "Any known compatibility issues between 10.04 and SIL 3114 sata cards?"
date: 2010-05-23
forum: Hardware
---

### Post by nstolting on 2010-05-23
I've been using Ubuntu since 7.10 without too many problems. Recently I wanted to add additional drives to my desktop machine (Asus P5N-D mobo). Limited on the number of SATA ports I bought a cheap SATA card (SIL 3114 chipset) so that I could plug 4 hard disks on to the motherboard and plug my eSATA and DVD into the Sata card.

I configured the 4 disks to have an individual /boot partition (located on SDA) and then created two (software) RAID10 partitions one for / and the other to act as swap.

Ubuntu installs correctly, but when I have the DVD player plugged into the SATA card, Ubuntu fails to boot, where the grub2 loader should be, all I get is a flashing cursor in the top left corner of the screen. If I remove the DVD player and eSATA connection from the SATA card, Ubuntu boots fine. 

Additionally, If I connect the DVD player to the SATA card and leave the live CD in the DVD player (without moving the card up in the BIOS boot order), Ubuntu will load correctly from the local hard disks.

I keep thinking this may be a bios configuration but I've tried everything, the boot order is 'removable', 'hard disk', 'SATA card'. I've tried the boot from PCI device setting but enabling or disabling that feature didn't have any effect on the bootabillity of the system.

Once booted the SIL 3114 card appears to be detected correctly and is usable as I performed the 10.04 install using the live CD via the DVD player connected to the SIL 3114 card.

I've just read that the SIL 3114 card doesn't play nicely with Ubuntu, is this really the case, should I look for a promise based card.

Currently I've disconnected the DVD player thinking that I can install and run most things via a USB drive.

Thanks in advance for any suggestions

Nigel Stolting

---

### Post by purduephotog on 2010-06-19
> **nstolting said:**
> I've been using Ubuntu since 7.10 without too many problems. Recently I wanted to add additional drives to my desktop machine (Asus P5N-D mobo). Limited on the number of SATA ports I bought a cheap SATA card (SIL 3114 chipset) so that I could plug 4 hard disks on to the motherboard and plug my eSATA and DVD into the Sata card.

I configured the 4 disks to have an individual /boot partition (located on SDA) and then created two (software) RAID10 partitions one for / and the other to act as swap.

Ubuntu installs correctly, but when I have the DVD player plugged into the SATA card, Ubuntu fails to boot, where the grub2 loader should be, all I get is a flashing cursor in the top left corner of the screen. If I remove the DVD player and eSATA connection from the SATA card, Ubuntu boots fine. 

Additionally, If I connect the DVD player to the SATA card and leave the live CD in the DVD player (without moving the card up in the BIOS boot order), Ubuntu will load correctly from the local hard disks.

I keep thinking this may be a bios configuration but I've tried everything, the boot order is 'removable', 'hard disk', 'SATA card'. I've tried the boot from PCI device setting but enabling or disabling that feature didn't have any effect on the bootabillity of the system.

Once booted the SIL 3114 card appears to be detected correctly and is usable as I performed the 10.04 install using the live CD via the DVD player connected to the SIL 3114 card.

I've just read that the SIL 3114 card doesn't play nicely with Ubuntu, is this really the case, should I look for a promise based card.

Currently I've disconnected the DVD player thinking that I can install and run most things via a USB drive.

Thanks in advance for any suggestions

Nigel Stolting

Same problem.

I had been running this just fine under 8x, and when I upgraded I turned on the SIL controller.  Could install just fine, but can't get past the init screens.

Turned it off, still having problems, calling it a night.

---

### Post by purduephotog on 2010-06-19
I have a solution!

Of course, you may not like it.  It worked for me, however, and seeing as this is a plus in my book, I'll share it.

I can't take credit for it:

First, read this little thread for background:
[http://forums.nvidia.com/index.php?showtopic=13942](http://forums.nvidia.com/index.php?showtopic=13942)

Then read this thread and download the 5.4.03 SIL 3114 bios.  You're going to want the 5403.bin file, not the other ones (double check the readme, however, in case you're not using the motherboard chipset- ie, this won't work for an add-in card).

Then read this page to set up a USB flash boot drive (or burn a CD, whichever you want).
[http://forums.mydigitallife.info/threads/8909-Make-A-bootable-USb-drive-For-Flashing-From-DOS](http://forums.mydigitallife.info/threads/8909-Make-A-bootable-USb-drive-For-Flashing-From-DOS)

Download the Award Bios Editor
[http://sourceforge.net/projects/awdbedit/files/awdbedit/awdbedit-1.0/awdbedit-1.0_bin.zip/download](http://sourceforge.net/projects/awdbedit/files/awdbedit/awdbedit-1.0/awdbedit-1.0_bin.zip/download)


Now download the up to date or latest firmware for your motherboard.  Alternatively you can get the latest awdflash utility and download your bios to the usb drive, then edit it.

What you're going to do is go load the bios from your motherboard into the Bios Editor and find the section that deals with the SIL 3114 chipset.  You'll see it as the bios number- 5139.  Mine was under PCI devices.

There is an option to 'replace' (mouseover the little chip icons).  When you find the 5139.bin file, replace it with the 5403.bin file that you downloaded from the SIL website.

I made a modification to the text of the bios (Since i have the A8N-SLI Premium 1303, it says -MOD now).

Write that bios to file (no more than 8 chars to be sure) and then save that to your bootable USB drive.

Boot the system using the usb drive, flash the bios, and reboot.

My system now recognizes the all attached drives to the SIL 3114 controller- these are the 2tb WDEARS drive.

Good luck.

ps- if you hose your system, I'm not responsible- just saying....

---

