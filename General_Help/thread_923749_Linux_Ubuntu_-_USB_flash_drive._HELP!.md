---
title: "Linux Ubuntu - USB flash drive. HELP!"
date: 2008-09-18
forum: General Help
---

### Post by JamesThePoet0 on 2008-09-18
Basically i've tried to put in this USB stick. It doesn't even register the damn thing!

What can I do?

Thanks.

---

### Post by kk0sse54 on 2008-09-18
Do you mean that you tried installing Ubuntu on a USB flash drive? If so you have to make sure that your bios is able to boot from usb.

---

### Post by mb_webguy on 2008-09-18
Or are you saying that you inserted a USB drive, and Ubuntu didn't automatically mount it?

If so, insert the USB drive and then post the output of the command "sudo fdisk -l".

---

### Post by JamesThePoet0 on 2008-09-18
> **C!oud said:**
> Do you mean that you tried installing Ubuntu on a USB flash drive? If so you have to make sure that your bios is able to boot from usb.

No mate! I mean, i've just bought a brand new USB flash drive, 2 GB, and i'm trying to put it into my Linux Ubuntu laptop, but absolutely nothing is happening!

---

### Post by JamesThePoet0 on 2008-09-18
> **mb_webguy said:**
> Or are you saying that you inserted a USB drive, and Ubuntu didn't automatically mount it?

If so, insert the USB drive and then post the output of the command "sudo fdisk -l".

james@ubuntu:~$ sudo fdisk -1
[sudo] password for james: 
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by mb_webguy on 2008-09-18
That was an "l", as in a lowercase "L", and not a "1".  Try just copying "sudo fdisk -l" and pasting it into the terminal with Ctrl-Shift-V.

---

### Post by JamesThePoet0 on 2008-09-18
> **mb_webguy said:**
> That was an "l", as in a lowercase "L", and not a "1".  Try just copying "sudo fdisk -l" and pasting it into the terminal with Ctrl-Shift-V.

My bad, thanks.

james@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x2c102d96

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6200    46871968+  83  Linux
/dev/sda2            6201        6717     3908520   82  Linux swap / Solaris
/dev/sda3            6718       20673   105507360   83  Linux

---

### Post by mb_webguy on 2008-09-18
Huh.  That's odd.  That's with the USB drive plugged in?

Have you used other USB drives successfully before?  What version of Ubuntu are you using?

---

### Post by JamesThePoet0 on 2008-09-18
> **mb_webguy said:**
> Huh.  That's odd.  That's with the USB drive plugged in?

Have you used other USB drives successfully before?  What version of Ubuntu are you using?

I think it was fully in, although the light wasn't on.

I've never actually used the USB drives till now! Ubuntu 8.0 - the Hardy Heron - released in April 2008 -> that's the one I have.

---

### Post by JamesThePoet0 on 2008-09-18
james@ubuntu:~$ sudo fdisk -l
[sudo] password for james: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x2c102d96

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6200    46871968+  83  Linux
/dev/sda2            6201        6717     3908520   82  Linux swap / Solaris
/dev/sda3            6718       20673   105507360   83  Linux

Disk /dev/sdb: 2000 MB, 2000748032 bytes
64 heads, 63 sectors/track, 969 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         969     1953439+   6  FAT16

-That looks different!-

---

### Post by mb_webguy on 2008-09-18
Have you *ever* used any USB device on this computer before now?  Do you have any other USB devices you could plug in to see if your USB port is even working?

Like all hardware, sometimes USB hubs go bad.  It's happened to me before.  If you're on a desktop, this isn't much of a problem because a USB PCI card is fairly inexpensive.  On a laptop, however, the USB ports are typically hardwired to the motherboard.  If the integrated USB hub goes bad on a laptop, you're pretty much screwed.  If you are on a laptop, and you have a PC card slot, you can get a USB to PC card adapter, which is basically a USB port that plugs into your PC card slot.  They're also relatively inexpensive, but not exactly convenient.

---

### Post by mb_webguy on 2008-09-18
Ah.... I just saw your last post.  Yes, that looks a bit different!  Did the USB drive mount automatically this time?  If not, now that it's actually being detected, we can at least mount it manually.

---

### Post by JamesThePoet0 on 2008-09-18
> **mb_webguy said:**
> Have you *ever* used any USB device on this computer before now?  Do you have any other USB devices you could plug in to see if your USB port is even working?

Like all hardware, sometimes USB hubs go bad.  It's happened to me before.  If you're on a desktop, this isn't much of a problem because a USB PCI card is fairly inexpensive.  On a laptop, however, the USB ports are typically hardwired to the motherboard.  If the integrated USB hub goes bad on a laptop, you're pretty much screwed.  If you are on a laptop, and you have a PC card slot, you can get a USB to PC card adapter, which is basically a USB port that plugs into your PC card slot.  They're also relatively inexpensive, but not exactly convenient.

See my post before this - it might be a different outcome now.

---

### Post by JamesThePoet0 on 2008-09-18
> **mb_webguy said:**
> Ah.... I just saw your last post.  Yes, that looks a bit different!  Did the USB drive mount automatically this time?  If not, now that it's actually being detected, we can at least mount it manually.

It's strange, it seems that if all freezes up.. How do I mount it manually?

---

### Post by JamesThePoet0 on 2008-09-18
mate?

---

### Post by ju2wheels on 2008-09-18
Out of curiosirty is your fstab preventing auto mounting of this thing by any chance?

Could you post the output of the following:
```

more /etc/fstab

```

---

### Post by mb_webguy on 2008-09-19
> **JamesThePoet0 said:**
> It's strange, it seems that if all freezes up.. How do I mount it manually?

Sorry, I thought you'd solved the problem.  To mount it manually, type "sudo mkdir /media/MyUSB; sudo mount -t vfat /dev/sdb1 /media/MyUSB".  You can, of course, change "/media/MyUSB" to any other location in your filesystem, though external devices are typically mounted in either /mnt or /media.

---

### Post by JamesThePoet0 on 2008-09-19
james@ubuntu:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8081662e-4b98-465d-8351-a006f533eaea /               ext3    relatime,error
s=remount-ro 0       1
# /dev/sda3
UUID=1366abee-e481-49e9-93b3-4a462acd53a6 /home           ext3    relatime      
  0       2
# /dev/sda2
UUID=3a296317-ccb1-40b5-9920-d1a1931929e0 none            swap    sw            
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda2 /mnt/ipod vfat user,noauto,umask=000 0 0
/dev/sdc2 /media/iPod vfat nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,us
er,defaults,noatime,iocharset=utf8 0 0


james@ubuntu:~$ sudo mkdir /media/MyUSB; sudo mount -t vfat /dev/sdb1 /media/MyUSB
mkdir: cannot create directory `/media/MyUSB': File exists
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

( Oh dear =( )

---

