---
title: "[SOLVED] CD and USB cannot be mounted after upgrade"
date: 2008-12-21
forum: Hardware
---

### Post by barmaley on 2008-12-21
Hello, ubuntu people
I need your help. Here is my problem that I cannot solve myself.

After upgrade to ubuntu 8.10 I cannot mount usb key. It did not bother me too much, but now it appears I cannot use any CD, even Live CD to boot from it. I need to add, that I can see DVD's, and as I noticed they are mounted in /media. Before the upgrade everything worked.
I don't know what is the reason, but I suspect that my configurations are messed up, including fstab, which I show here to begin with:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=51e0c37b-2da4-48ce-8134-c4f60b377997 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/hda2
UUID=f87298f4-48c5-40b8-815c-6e11daae5fde none            swap    sw              0       0

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I searched through this forum and saw some similar problems, but none of them helps me. Any help from you is appreciated.

To be more informative here is the output of "sudo lshw -C disk", which shows some problem with CD:
*-disk                  
       description: ATA Disk
       product: WDC WD2500JB-55R
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 20.0
       serial: WD-WCANKH678219
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0000a6e5
  *-cdrom
       description: DVD-RAM writer
       product: DVD-RAM GSA-H55N
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.03
       serial: [HL-DT-STDVD-RAM GSA-H55N1.0307/10/11 7U02
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

Thank you in advance.

---

### Post by barmaley on 2008-12-25
All problems were solved.
CD/DVD Rom is broken.
USB works fine in USB-1 mode, I just disable USB-2 mode in the BIOS.

End of story.

---

