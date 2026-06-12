---
title: "Request help editing Fstab"
date: 2007-08-23
forum: Hardware &amp; Laptops
---

### Post by derba on 2007-08-23
Hello everyone,

Im a bit of a beginner so step-by-step instructions are much appreciated.

Ive recently moved my home box over to Ubuntu (my last Windows machine; Im now 100% Linux :)) and I ran into a bit of unfamiliar territory.

I have two SATA drives in my home box, each with one partition. I have Ubuntu installed on one with the complete file system and I plan on using the second drive exclusively for data storage.

I would like the second drive to automount. I searched around for tutorials and couldn't find any that actually supplied steps to do this - I assume because it's so simple everyone knows how to do it :)

Many sites I found pointed the user to System -> Preferences -> Removable Drives and Media; this is not an external SATA drive, the drive is internal.

Many other sites noted that Fstab needed to be edited to see the volume on boot; none I found supplied how to edit this file correctly. I dont know when the last time those commenters opened Fstab was but mine is dauntingly complex and not self-explanatory in the least.

Thanks in advance for any suggestions!

P.S. I did search this forum for a thread that supplied what I needed but could find none - If your search-fu is stronger than mine please link and I will bow humbly to your prowess...

---

### Post by merlinus on 2007-08-23
Post results of:

```

sudo fdisk -l
mount
cat /etc/fstab

```-merlin

---

### Post by derba on 2007-08-25
Apologies for the lengthy reply time. Here are the requested results:

```

cj@Rogue Encampment:~$ sudo fdisk -l
Password:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161   83  Linux
cj@Rogue Encampment:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb1 on /media/Warehouse type ext3 (rw,noexec,nosuid,nodev)
cj@Rogue Encampment:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d00a0a07-4d83-4e2f-a32f-e0f5d5eb4d32 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=0bb94ec7-b7f6-4f2c-bcbd-5014140b7a14 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
cj@Rogue Encampment:~$ 

```

---

### Post by dragonwings on 2007-08-25
im using ubuntu 7.04 and have never had such a problem

i would think it would be a bios matter 

or 

setting the hard drive to slave or cableselect  with jumpers on hard drive

hope this helps

---

### Post by merlinus on 2007-08-25
Try adding this line to /etc/fstab.  From the output of mount, it looks like it is mounted.

/dev/sdb1 /media/Warehouse ext3 defaults 0 1

-merlin

---

### Post by derba on 2007-08-26
I dont think it's a BIOS matter, it sees both drives; and they're both SATA drives which don't require jumpers to set cable select mode.

The drive was mounted at the time of the output I posted but I mounted it myself manually after the OS fully booted. Ubuntu sees the volume upon boot but does not automatically mount it and asks me for a password every time I mount it.

This wouldn't normally bother me but mounting it like that is one extra step for me and programs that use that drive (like Rythymbox accessing my music) throw errors if I forget to mount that volume before I run the program.

---

### Post by logos34 on 2007-08-26
did you try what Merlinus just suggested?  Add it and reboot.  It should automount.

---

### Post by derba on 2007-08-26
merlinus, I bow to you sir

amending my fstab with that line worked solidly.

much appreciated!

---

