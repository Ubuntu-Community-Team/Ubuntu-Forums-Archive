---
title: "Migrating HDs"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by alphadelta14 on 2009-07-08
Its been quite an experience over the past 2 days. I've been trying to move my Ubuntu installation to a 40 gig HD from a 20 gb one. What I ended up doing was reinstalling 9.04 onto the 40 gb one. Then I tarballed my home folder, var, etc, lib, tmp, and usr and extracted them into my new install. So now I have my exact environment (with an updated kernel). My original HD was in my Slave spot with a Master Windows XP Drive. So when i moved everything, it became the Master, with the new one in the Slave Drive Position. I did have to reinstall GRUB though. Currently I cannot mount my Windows Disk at all. I can't even load it. I have some weird GRUB problem with it. I did accidentally install a GRUB version to it when I was migrating. I didn't look at it at the time, but I went in with the Install CD (for XP) and did a fixmbr. It currently says "GRUB _" when I try to boot from it (It has a blinking cursor, but doesn't allow any input). GParted gives a small error to /dev/sda2 (I don't wanna partition it) saying "Unable to read contents of this filesystem! Because of this, some operations may be unavailable." Fstab interestingly enough gives me a "# Entry for /dev/ !! UNKNOW DEVICE !! :" for my Ubuntu drives (/dev/sdb?) and nothing for my /dev/sda? drives. fdisk -l returns this:
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5        4862    39021885    7  HPFS/NTFS

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00081326

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4787    38451546   83  Linux
/dev/sdb2            4788        4998     1694857+   5  Extended
/dev/sdb5            4788        4998     1694826   82  Linux swap / Solaris

Trying to mount it in terminal (sudo mount /dev/sda2 -t ntfs /mnt/disk [-o force]) returns:
Unexpected clusters per mft record (-128).
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?


So basically what I am going after is how can I get to my Windows Drive?
It does in fact exist. F2 setup (Dell i386 Desktop) says that there is a Drive that is there.

---

### Post by az on 2009-07-08
You may have blown away the NTFS Boot sector when you installed GRUB to the wrong partition.  See this:

[http://ubuntu-rescue-remix.org/node/57](http://ubuntu-rescue-remix.org/node/57)

---

### Post by alphadelta14 on 2009-07-09
I have now fixed my NTFS partition (it needed a valid boot sector). And now it is very much mountable, but I cannot boot into it because the random "GRUB _" is still there. I did do the fixmbr, with no sucess (it returned a success message though, but GRUB remains.)

So now I need tips on how to remove this GRUB, without the fixmbr.

EDIT:
fdisk /mbr also failed, but I went back to the OS Disk and saw fixboot, which did the trick. I'm finally all good! (don't know why I'm so excited about having windows though...)

---

