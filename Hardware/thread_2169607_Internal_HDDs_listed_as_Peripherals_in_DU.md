---
title: "Internal HDDs listed as Peripherals in DU"
date: 2013-08-22
forum: Hardware
---

### Post by matt19 on 2013-08-22
[COLOR=#333333][FONT=UbuntuRegular]Why would my HDDs and DVD drives be installed as peripheral devices in disk utility?[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I'm attempting to set up a file server using 12.04, but don't want to initiate a ZFS pool until I'm sure the drives are being read & set up properly. Most importantly, why is this happening? And a distant second, will this affect the ZFS setup?[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I've reinstalled a few times via an ubuntu created USB drive using different options (auto-partition option and various custom partition options) and it continues to occur.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]My boot drive is a 640gb with MBR and a 120gb os partition, 1 6.4gb swap and 1 6.4gb extended partition. I'm not dual-booting since this will be a file server. I have 3 2TB drives, a 1.5 TB drive, the 640gb boot drive, as well as a 30gb USB drive (for install), an IDE DVDROM drive and a non-existent floppy drive all listed under 'Peripheral Devices' in Disk Utility.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Is it due to the MBR boot sector or some other install option?[/FONT][/COLOR]

---

### Post by BuntuSeriously on 2013-08-22
I'm certainly no expert here, but, if you have enough RAM on your box, you might in the future consider installing with just a small(ish) ext2 /boot and a straightforward ext4 / as the rest.  Some will disagree, but do toss the swap.  It will make a substantial difference...

FWIW, I've installed Xubuntu for two years now with these setup constraints and have had no problems whatsoever.

Finally, if the issue you're experiencing is ultimately traceable to a corrupt USB install, I recommend the USB setup for ISOs available via the [PartedMagic]("http://sourceforge.net/projects/partedmagic/") distro/tool.  Again, a rock-solid starting point is the goal for us all; and this tool will not disappoint --

Hope this helps at some point in your venture.


Cheers ;)

---

### Post by matt19 on 2013-08-24
I gave that a shot & still no luck.  I've also tried disconnecting all other SATA drives on install via USB and DVD.  I've also tried forcing GPT partitioning through reformatting with gparted and custom partitioning on install.

In case posting my fstab and /dev/disk/by-id dir would help, here it goes.  Anything else I can post to get some additional help on this?

I also thought about removing swap, but this is a file server that I hope to use with a ZFS pool. My impression is that for max stability, I should have a swap.  I have 6gb of RAM, 7.5 tb of total storage space (4 + 1.5 after raidz1).

My concern (when plugged in my 4 storage HDDs are located under peripherals also ):
[IMG]http://farm4.staticflickr.com/3819/9586268512_6a986a4457.jpg[/IMG]

fstab:

> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=dc5031f7-3a0a-4649-bd28-bacd14e6e421 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=358b541d-5ddc-4a78-994a-17e246fe94da none            swap    sw              0       0



/dev/disk/by-id:
> total 0
drwxr-xr-x 2 root root 300 Aug 24 13:33 .
drwxr-xr-x 5 root root 100 Aug 24 13:33 ..
lrwxrwxrwx 1 root root   9 Aug 24 13:33 ata-TSSTcorp_CDDVDW_SH-S223L_0h23H56789ULMNOP -> ../../sr0
lrwxrwxrwx 1 root root   9 Aug 24 13:33 ata-WDC_WD6400AAKS-65A7B0_WD-WMASY2773008 -> ../../sda
lrwxrwxrwx 1 root root  10 Aug 24 13:33 ata-WDC_WD6400AAKS-65A7B0_WD-WMASY2773008-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 Aug 24 13:33 ata-WDC_WD6400AAKS-65A7B0_WD-WMASY2773008-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 Aug 24 13:33 ata-WDC_WD6400AAKS-65A7B0_WD-WMASY2773008-part5 -> ../../sda5
lrwxrwxrwx 1 root root   9 Aug 24 13:33 scsi-SATA_WDC_WD6400AAKS-_WD-WMASY2773008 -> ../../sda
lrwxrwxrwx 1 root root  10 Aug 24 13:33 scsi-SATA_WDC_WD6400AAKS-_WD-WMASY2773008-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 Aug 24 13:33 scsi-SATA_WDC_WD6400AAKS-_WD-WMASY2773008-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 Aug 24 13:33 scsi-SATA_WDC_WD6400AAKS-_WD-WMASY2773008-part5 -> ../../sda5
lrwxrwxrwx 1 root root   9 Aug 24 13:33 wwn-0x50014ee000ca6fa2 -> ../../sda
lrwxrwxrwx 1 root root  10 Aug 24 13:33 wwn-0x50014ee000ca6fa2-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 Aug 24 13:33 wwn-0x50014ee000ca6fa2-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 Aug 24 13:33 wwn-0x50014ee000ca6fa2-part5 -> ../../sda5



---

### Post by BuntuSeriously on 2013-08-26
Sorry it took a while to get back with you.

Looks like you're going to need a talented cutter to help out with this.  The whole things seems rather strange to me.

The last thing I would try in your predicament (everything else having failed) is looking at some sort of BIOS issue.  If you're still seeing an odd drive population on a fresh install *even after devices are unplugged*, you've got to be getting this corrupted data from somewhere.  Firmware would seem to be all that's left to steer you wrong.

That's about all I could do in your shoes.  Hopefully someone with much greater insight can come along and offer more tangible help . . .

---

### Post by rsbrux on 2013-11-02
> **matt19 said:**
> [COLOR=#333333][FONT=UbuntuRegular]Why would my HDDs and DVD drives be installed as peripheral devices in disk utility?[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular][/FONT][/COLOR]
The original question here seems still to be unanswered.
Perhaps it is in the wrong section?
IAC, I have the same question:
All of my internal SATA drives (4 x HDD + 1 x DVD) are listed in the Ubuntu 12.04 Disk Utility under Peripheral Devices (USB, FireWire and other peripherals).
They all seeem to work fine, so this is only a minor annoyance; still, it irritates me.
Perhaps the cause is indeed at a deeper level than the OS, as I have also seen Windows 7 report internal SATA drives as "removable".
Why do these drives appear this way?
Is there any way to make them appear as they should?

---

