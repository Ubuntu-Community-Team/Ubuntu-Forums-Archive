---
title: "Installing GRUB on it's own partition - 8.10 installation problem"
date: 2009-01-08
forum: Installation &amp; Upgrades
---

### Post by lewisskinner on 2009-01-08
Hi all, and a Happy New year to everyone!

I have a multi-boot system, with Vista and Ubuntu on Primary partitions, and an extended partition consisting of 4 ext3 partitions, for testing OSs (these are reformatted as necessary, ie to UFS, Reiser, XFS etc).  I also have a small (1MB) partition for GRUB.

My hope, is that I can install Ubuntu mounting sda2 as /boot/grub, and then if (when) I install a third OS, can take a copy of the sources.list file, install the new OS (again mounting sda2 as /boot/grub) and then merge the two sources.list files, however, when I tried to install 8.10, I got an error.

Here is my partition table by the way, including the mount points I attempted to use:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6d242da1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       33192   266614708+   7  HPFS/NTFS     **/windows**
/dev/sda2           33193       33193        1024   83  Linux  **/boot/grub** (note, this is formatted as ext2)
/dev/sda3           33193       52773   157283358+  83  Linux  **/ (root)**
/dev/sda4           52774       60801    64484910    5  Extended
/dev/sda5           52774       54927    17301973+  83  Linux  *unmounted*
/dev/sda6           54928       56885    15727603+  83  Linux  *unmounted*
/dev/sda7           56886       58843    15727603+  83  Linux  *unmounted*
/dev/sda8           58844       60801    15727603+  83  Linux  *unmounted*

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d7afc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         653     5245191    b  W95 FAT32  *unmounted*
/dev/sdb2             654        1306     5245222+  82  Linux swap / Solaris  **SWAP**
/dev/sdb3            1307       61454   483138810    7  HPFS/NTFS  **/shared**
/dev/sdb4           61455      121601   483130777+  83  Linux **/home**

Any ideas?

---

### Post by logos34 on 2009-01-08
> **lewisskinner said:**
> 
My hope, is that I can install Ubuntu mounting sda2 as /boot/grub, and then if (when) I install a third OS, can take a copy of the sources.list file, install the new OS (again mounting sda2 as /boot/grub) and then merge the two sources.list files, however, when I tried to install 8.10, I got an error.

Any ideas?

Not sure exactly what happened during installation of 8.10, but if you're just making Grub (not full /boot) partition on sda2 (and 1 MB should be enough for the contents of /boot/grub), then you don't even need to point the ubiquity installer to it--just indicate /, /swap and /home.

After you reboot [follow this guide]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_") to making a so-called 'dedicated grub partition.' (Basically you just copy grub files, reinstall bootloader pointing to it and add line to fstab).  

Then you can add entries to chainload other OSs, or use [configfile ]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile")method.

---

### Post by lewisskinner on 2009-01-08
Ah!  That looks very sensible!

I'll have a go at that and report back

---

### Post by lewisskinner on 2009-02-27
> **lewisskinner said:**
> Ah!  That looks very sensible!

I'll have a go at that and report back

This works - thanks very much for the pointer!

---

