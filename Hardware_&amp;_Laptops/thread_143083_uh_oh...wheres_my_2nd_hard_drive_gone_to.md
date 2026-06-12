---
title: "uh oh...wheres my 2nd hard drive gone to?"
date: 2006-03-11
forum: Hardware &amp; Laptops
---

### Post by darkwings on 2006-03-11
hey all, just made the switch up from hoary to breezy...after a few glitches with the monitor being out of synch...(thanks to all that posted the ctrl + alt + f1 to get the command line) im up and running...sound is running and video is a-ok...
but now i fear i might have actually wiped out my 2nd hard drive...during the install process i was asked what i wanted it to do with my partitions...i told it to wipe out my primary drive and that was it...do i have to remount it?...i thot it would still be there after the "detecting hardware" thing...

yes its longwinded and yes im still quite a noob...but after thoroughly beating the stuffing out of hoary i decided to plunge in and try this on my own...(a very good friend put hoary in my machine for me as i was fairly certain of something going wrong...but hes really really busy lately and said with a great sigh...just go and try it your self...i think you'll be surprised

so far i am.......but i need to find my 2nd drive...help help help

p.s. thanks in advance for putting up with this banter peace

---

### Post by xmastree on 2006-03-11
It's probably there but not mounted. First thing to do is this:
**sudo fdisk -l**
which will list all disks and their partitions, mounted or not.
Then do:
**mount**
which will tell you what's mounted. Your second disk probably isn't there.

What you do next depends on where your second disk is, and how it's partitioned and formatted. You will need to make a mount point, something like /mnt/disk2 then add a line to your etc/fstab to make the disk mount there at boot. Or you can mount it manually. Either way you need to know which disk (hda,hdb,hdc,hdd) and the partitions/filesystems it contains.

---

### Post by darkwings on 2006-03-13
ok well i did fdisk and got:

Disk /dev/hda: 8399 MB, 8399978496 bytes
255 heads, 63 sectors/track, 1021 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         975     7831656   83  Linux
/dev/hda2             976        1021      369495    5  Extended
/dev/hda5             976        1021      369463+  82  Linux swap / Solaris

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       19457   156288321   83  Linux


so its showing up right?

then i did mount and got:

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
/dev/hdb1 on /mnt/storage type ext3 (rw)

i added the mnt point in fstab with sudo...but i still cant write to the disk...i use this for my downloads and for file sharing...i know its something simple...ugh what am i missing...help help

dw

****EDIT - its working now, i have no idea what i did, perhaps rebooting the machine and threatening to spill coffee on it worked :)...thanks for your advie xmas, muchly appreciated...WOOT WOOT****

---

