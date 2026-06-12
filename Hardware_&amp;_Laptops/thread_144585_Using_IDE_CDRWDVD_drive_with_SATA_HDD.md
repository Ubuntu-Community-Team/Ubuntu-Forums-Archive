---
title: "Using IDE CDRW/DVD drive with SATA HDD"
date: 2006-03-14
forum: Hardware &amp; Laptops
---

### Post by bjtuna on 2006-03-14
I have a Dell Dimension 4700. The primary HDD is running in SATA mode, which I presume is using libata; it appears in Linux as /dev/sda. However the CDRW/DVD drive is plain old IDE/ATAPI and it's not appearing as a device in my Linux system.  Any help would be appreciated. Thanks!

---

### Post by localzuk on 2006-03-14
Hi, could you post your /etc/fstab to us? Also, could you tell us if the cd/dvd is the only PATA(IDE) drive (and if it isn't, which settings it has - ie. primary master, primary slave, secondary master or secondary slave)?

---

### Post by bjtuna on 2006-03-14
[QUOTE=localzuk]Hi, could you post your /etc/fstab to us? Also, could you tell us if the cd/dvd is the only PATA(IDE) drive (and if it isn't, which settings it has - ie. primary master, primary slave, secondary master or secondary slave)?[/QUOTE]

fstab doesn't matter, because dmesg isn't showing it being detected as a device (I would have expected it to be hda). 

In the BIOS, the HDD is configured on SATA-0 and the CD/DVD drive is configured as IDE-0 (PATA), primary master.

In my kernel I have the following enabled:
- IDE/ATA-2 DISK support
- IDE/ATAPI CDROM support
- SCSI emulation support
- SCSI disk support
- SCSI generic support

---

### Post by localzuk on 2006-03-14
Hmm... Bizarre.[/blunt]

What type of motherboard chipset are you on?

---

### Post by bjtuna on 2006-03-14
i believe it's the intel 915G chipset.

---

### Post by localzuk on 2006-03-14
After having a quick skeet for 'intel ide chipset' I came across a thread referencing this: [http://www.ubuntuforums.org/showthread.php?t=25217](http://www.ubuntuforums.org/showthread.php?t=25217)

It appears you have to change a setting in the bios from ahci to ata - as it is a hardware/driver related issue... Hope this helps

---

