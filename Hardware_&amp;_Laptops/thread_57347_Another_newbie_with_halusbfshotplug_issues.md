---
title: "Another newbie with hal/usbfs/hotplug issues"
date: 2005-08-16
forum: Hardware &amp; Laptops
---

### Post by LiveStatic on 2005-08-16
I have spent the last five days learning how to install, work with and configure my first Linux desktop with only what I've been able to glean from google searches and this forum (thanks, by the way, to all those users who respond to these maladies) for aid. I've looked around (though I might not know *where* to look) for any method to help me, but though I've found many helpful threads here to solve my system's more obvious problems, I haven't yet been able to repair this particular problem, despite my best (unknowledgeable) attempts.

When I first installed Ubuntu, my USB mass storage devices would automount and worked perfectly. Now whenever I plug in my flash mp3 player or my 128MB flash drive, I get nothing. Not only that, nearly half the time when I login, hal fails to start! A quick ctrl alt F1 and I was ready to go after restarting gdm from the terminal screen, but recently, this method has stopped working. The screen simply goes blank and my monitor recieves no input, forcing me to hard reset (which only causes hal to screw up even more often, apparently). This might have something to do with those ati drivers I installed, perhaps?

My USB mouse still functions perfectly fine. I've tried reinstalling the hal package (as well as nearly every package that has anything to do with USB and usbfs) through synaptic, but it doesn't fix anything. lsusb just hangs. I can access /proc/bus/usb throug the command line, but I cannot open any of the files within, it just hangs using gedit or nano. Accessing /proc/bus/usb in nautilus just brings up a blank folder than never finishes loading. I can umount usbfs, but not mount it back up. When I do unmount it, /proc/bus/usb/ is simply empty (probably how it should be, but I'm not sure).

My mp3 player shows the USB version when plugged in (regardless of wether or not my pc chooses to recognise it). Sometimes the mp3 player displays USB v1.1 and sometimes it displays USB v2.0. When booting, hotplug hangs indefinitely when booting if USB flash drive is connected. I've read that the USB drive is often mapped to a SCSI drive, but I don't see and sda's, sdb's or whatever in /dev/ .

I'm running a bit of a strange dual boot set-up with WinXP as my other OS.
**Output of fdisk -l:**
Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4997    40138371    7  HPFS/NTFS

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       10942    87891583+   7  HPFS/NTFS
/dev/hdb2   *       10943       14440    28097685   83  Linux
/dev/hdb3           14441       14593     1228972+   5  Extended
/dev/hdb5           14441       14593     1228941   82  Linux swap / Solaris


I'm not really sure what data to give you or how to get it. The command line's more mysterious and powerful functions are still unknown to me.

**/etc/fstab:**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
/dev/hdb1       /media/windows2  ntfs    nls=utf8,umask=0222 0       0

**/etc/mtab:**
/dev/hdb2 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
/dev/hda1 /media/windows ntfs rw,nls=utf8,umask=0222 0 0
/dev/hdb1 /media/windows2 ntfs rw,nls=utf8,umask=0222 0 0
/dev /.dev unknown rw,bind 0 0
none /dev tmpfs rw,size=5M,mode=0755 0 0
usbfs /proc/bus/usb usbfs rw 0 0

**mount/umount test:**
livestatic@LiveStatic:~$ mount usbfs
mount: according to mtab, usbfs is already mounted on /proc/bus/usb
mount failed
livestatic@LiveStatic:~$ mount
/dev/hdb2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev/hda1 on /media/windows type ntfs (rw,nls=utf8,umask=0222)
/dev/hdb1 on /media/windows2 type ntfs (rw,nls=utf8,umask=0222)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)
livestatic@LiveStatic:~$ sudo umount usbfs
Password:
livestatic@LiveStatic:~$ mount
/dev/hdb2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev/hda1 on /media/windows type ntfs (rw,nls=utf8,umask=0222)
/dev/hdb1 on /media/windows2 type ntfs (rw,nls=utf8,umask=0222)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
livestatic@LiveStatic:~$ sudo mount usbfs
mount: can't find usbfs in /etc/fstab or /etc/mtab

---

### Post by LiveStatic on 2005-08-19
Well, I booted my XP partition and when I connect a USB flash drive Windows freezes completely. This no longer appears to be an Ubuntu-only problem, but I was wondering if this has happened to anyone here. I've messed with my BIOS a little, but nothing seems to have changed since when they worked and I used the utility included with my mobo to check my BIOS and it doesn't appear to be corrupted. What the hell?

---

### Post by Deusiah on 2005-08-19
I just had the same symptom where my USB iRiver was failing to be detected even after a restart. I killed HAL then restarted it as root and all was well. My CD drive lept into action along with my iRiver. I think it may have something to do with a recent upgrade perhaps?

---

