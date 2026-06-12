---
title: "Unable to access NTFS hard drive"
date: 2007-08-29
forum: Hardware &amp; Laptops
---

### Post by carbonic_killa on 2007-08-29
After installing ubuntu on my computer, i was messing around with grub in order to boot the ubuntu drive before my windows drive

Primary SATA -Windows
Primary Master - ubuntu

after hours of trying i was not successful so i just went to my BIOS and turned the hard drive off
Long story short, i attempted to access the windows drive today and got an "Unable to mount the volume" error while selecting the drive in ubuntu.  i went to terminal and entered dmesg | tail -

ubuntu@ubuntu:~$ dmesg | tail
[  152.125948] Bluetooth: L2CAP socket layer initialized
[  152.446915] Bluetooth: RFCOMM socket layer initialized
[  152.446931] Bluetooth: RFCOMM TTY layer initialized
[  152.446934] Bluetooth: RFCOMM ver 1.8
[  548.252114] NTFS driver 2.1.28 [Flags: R/O MODULE].
[  548.252955] NTFS-fs warning (device sdb2): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
[  548.260345] NTFS-fs warning (device sdb2): is_boot_sector_ntfs(): Invalid boot sector checksum.
[  548.260356] NTFS-fs error (device sdb2): read_ntfs_boot_sector(): Primary boot sector is invalid.
[  548.260362] NTFS-fs error (device sdb2): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[  548.260367] NTFS-fs error (device sdb2): ntfs_fill_super(): Not an NTFS volume.


results of fdisk -l
Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          62      497983+  82  Linux swap / Solaris
/dev/sda2              63         670     4883760   83  Linux
/dev/sda3   *         671         925     2048287+  83  Linux
/dev/sda4             926       24792   191711677+   b  W95 FAT32

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           5       40131   de  Dell Utility
/dev/sdb2   *           6       19452   156208027+   7  HPFS/NTFS
 ^ HD that is not mounting


How will i be able to fix this problem?

---

### Post by neouser99 on 2007-08-29
Everything that I came across points towards being SOL, which isn't good. Here is one example...
[http://www.linuxforums.org/forum/installation/41383-lost-ntfs-xp-parition-dual-boot-2.html](http://www.linuxforums.org/forum/installation/41383-lost-ntfs-xp-parition-dual-boot-2.html)

Sorry,
-neo

---

### Post by logos34 on 2007-08-29
Sounds like you may have 'disabled' the disk in the bios, but that normally only affects booting (which is why fdisk still shows it, it's spinning)...You did undo the changes in the bios, right?  

Were you perhaps 'messing around' with any other files like /etc/fstab?  (you might want to post it along with /boot/grub/menu.lst)

And can you still boot windows?

---

### Post by carbonic_killa on 2007-08-29
Thanks for the help so far guys

_fstab_

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=c9c80aae-0e0c-4ec2-a912-1aa4d36b2dc0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=b43d48e5-fdc3-48f6-9403-6125b586d847 /media/sda3     ext3    defaults        0       2
# /dev/sda4
UUID=46D4-5697  /media/sda4     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=07D4-060E  /media/sdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb2
UUID=80C2F69090FA0800 /media/sdb2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=80841b52-f34b-4b28-8b78-1c394c82798b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb3	/media/windows ntfs-fuse auto,gid=1001,umask=0002 0 0 <--my attempt to mount
/dev/sda3 	/home ext3 nodev,nosuid 0 2

_menu.lst_

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=c9c80aae-0e0c-4ec2-a912-1aa4d36b2dc0 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=c9c80aae-0e0c-4ec2-a912-1aa4d36b2dc0 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=c9c80aae-0e0c-4ec2-a912-1aa4d36b2dc0 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=c9c80aae-0e0c-4ec2-a912-1aa4d36b2dc0 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet


hmm interesting...after i re-installed ubuntu, Windows was no longer recognized, well that sucks...

edit: O, and yes. i did re enable the hard drive 
it seems like only the partition because a partition known as "dell something" (containing all service information) is detected in linux
If this problem is unable to be solved, can anyone hint to some REALLY good file recovery software

---

### Post by logos34 on 2007-08-29
ok, you need to clean up fstab...there's no 'sdb3' so that's gotta go...and what's up with sda3?--there are TWO entries and it's flagged as boot (rather than /) in fdisk...Did you create a separate /home partition AFTER install or what? (edit whatever it is it's pretty small).  Clarify.

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda2
UUID=c9c80aae-0e0c-4ec2-a912-1aa4d36b2dc0 / ext3 defaults,errors=remount-ro 0 1
[B]# /dev/sda3
UUID=b43d48e5-fdc3-48f6-9403-6125b586d847 /media/sda3 ext3 defaults 0 2[/B] [COLOR="Red"]??[/COLOR]
# /dev/sda4
UUID=46D4-5697 /media/sda4 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sdb1
UUID=07D4-060E /media/sdb1 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sdb2
UUID=80C2F69090FA0800 /media/sdb2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda1
UUID=80841b52-f34b-4b28-8b78-1c394c82798b none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
**/dev/sda3 /home ext3 defaults 0 2**  [COLOR="Red"]??[/COLOR]


You can add an entry for windows to menu.lst

---

### Post by carbonic_killa on 2007-08-29
ok, i commented out 

# /dev/sda3
UUID=b43d48e5-fdc3-48f6-9403-6125b586d847 /media/sda3 ext3 defaults 0 2

and yes, i did create a home dir after ubuntu the install, actually, i created it on the first install, reinstalled ubuntu and just linked the partition to use as home

---

### Post by logos34 on 2007-08-30
ok, so for sda3 just use the last entry in fstab (you can use 'defaults' in place of 'nodev,nosuid' if you want).

try that and see if everything mounts properly, including sdb2.   Then the next step is to add windows to menu.lst

EDIT: you could also try that sdb2 line with a '0' at the end (no check)

# /dev/sdb2
UUID=80C2F69090FA0800 /media/sdb2 ntfs defaults,nls=utf8,umask=007,gid=46 0 [COLOR="Red"]**0**[/COLOR]

---

### Post by carbonic_killa on 2007-08-30
"ok, so for sda3 just use the last entry in fstab"

What do you mean by "use"?

---

### Post by logos34 on 2007-08-30
I meant use this entry

**/dev/sda3 /home ext3 defaults 0 2**

And since you commented out the other entry

# /dev/sda3
[COLOR="Red"]#[/COLOR]UUID=b43d48e5-fdc3-48f6-9403-6125b586d847 /media/sda3 ext3 defaults 0 2

there should be no be no conflict.

---

### Post by carbonic_killa on 2007-08-30
ok, done. but it is still unable to recognize my windows partition. My main concern is to be able to access the drive so that i can back up the files.  Booting into windows would then be step 2.

---

### Post by logos34 on 2007-08-30
Maybe the guy above is right -- you're SOL:
> Device Boot Start End Blocks Id System
/dev/sdb1 1 **5 40131** de Dell Utility
/dev/sdb2 * **[COLOR="Red"]6 19452[/COLOR]** 156208027+ 7 HPFS/NTFS

They overlap.  The partition table is screwy.

Try recovery with [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").  Just be careful using it.  Make sure to read the documentation.

**sudo apt-get install testdisk** 

It's also included on most utility live CD's (like SystemRescueCD) if you want to run it that way.

---

