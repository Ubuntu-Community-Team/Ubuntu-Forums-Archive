---
title: "SCSI Problem?"
date: 2005-04-20
forum: Hardware &amp; Laptops
---

### Post by shaslinger on 2005-04-20
I am trying to install Ubuntu on an old PII 300 Siemens Nixdorf Server and fail at the very beginning.
After booting and entering linux aic7xxx=no_reset as boot parameters, which work fine with vanilla under Debian 3.0, I get only three more lines:

Loading /install/vmlinuz .....
Loading /install/initrd.gz .....
Ready.

Then the System hangs. I`ve also tried disabling acpi and apic.
Is there anybody out there with any clue what actually fails in my case?

Ciao,
Stefan

---

### Post by AlanQ on 2005-04-24
Hi shaslinger
Hope you don't mind me adding to your problem.
Anyone who can sort yours will probably know what's wrong with mine as well.

Last week my main PC died -- motherboard I think.

I didn't have a recent enough backup (I know... I know...)

I transferred the SCSI disk from that machine to a second one.

Configuration:

Motherboard: AMIBIOS version 08.00.09
SCSI controller: LSI Logic 1020/1030 MPTBIOS-IM-5.07.02
Primary IDE Master: Seagate ST320413A ~20GB
Secondary IDE Master: NEC DVD-RW ND-250
No Slaves

SCSI:
Controller at ID 7
Original disk: IBM IC35L036UWDY10-0S27Q -- 35003MB -- at ID 6
From other machine: Seagate ST318406LW -- 17501MB -- at ID 0

Due to physical constraints I moved the original SCSI disk from the end of the cable (adjacent to terminator) back two positions. And put the old SCSI disk on the end. So there is a 'plug' between them:

 The problem:

 WinXP on the IBM SCSI boots up fine and I can access my windows files.
 Don't know how to get XP to try to access other disks...

 Knoppix 3.7 on CD boots OK using SCSI driver aic7xxx.
 And I can access all partitions on all disks.
 This is how I transferred my files from the old Seagate disk.
 (Thank you, Knoppix. And thank you 'Linux User & Developer' magazine for the disk being on the front cover.)

 RedHat Fedora Core 3 (on hda2) gets as far as 'Red Hat nash version 4.1.18 starting' and then hangs.
 (Booted up and worked fine before: IDE and SCSI disks both mountable.)

 Ubuntu 4.10 (Warty Warthog -- 2.6.8.1-3-386 -- on hda1 -- (Debian)) boots OK, but when it puts it's tmpfs on /dev, there is no /dev/sd* AND no device for the floppy drive! Floppy was OK before.
 I can access the floppy by 'mnkod /dev/fd0 b 2 0' etc.
 But, when I 'mknod /dev/sda b 8 0'
 cfdisk, hexdump, and dd all report 'no such device', 'cannot open disk', etc.

 When I try to re-install Fedora Core 3 from DVD, it gets as far as installing a SCSI driver (aic7xxx followed by mptscsih) and then hangs.

 I do get an error during boot on Ubuntu.
 Had this before adding the old SCSI disk though, but it may be relevant:
 "
 PNPBIOS: Warning! Your PnP BIOS caused a fatal error. Attempting to continue
 PNPBIOS: You may need to reboot with the "nobiospnp" option to operate stably
 PNPBIOS: Check with your vendor for an updated BIOS
 PNPBIOS: get_dev_mode: unexpected status 0x28
 "

 (Don't know where to put "nopnpbios" in GRUB...? I've tried choosing software only plug'n'play in the motherboard bios, but it has no effect)

 Just noticed that sound in Ubuntu has gone as well!?
 Don't use sound much. But have even lost system bleep/bell.
 No sndconfig either, so can't follow advice in LinuxJournal letters page.

 Anyone...?

 Cheers
 Alan

 ps Any ideas on a good motherboard? :)

---

### Post by al7kz on 2005-04-26
corrected

---

### Post by AlanQ on 2005-04-27
Thanks, al7kz

> Isn't the pnpbios option in your board's bios setup program? Hit delete or whatever at boot to go into bios setup, then where it asks if the OS is pnp, say no or manual, depending on your bios.

I've done that. Still get the error message.

---

### Post by al7kz on 2005-04-27
corrected

---

