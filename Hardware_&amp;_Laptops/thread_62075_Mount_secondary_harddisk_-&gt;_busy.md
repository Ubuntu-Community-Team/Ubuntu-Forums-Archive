---
title: "Mount secondary harddisk -&gt; busy"
date: 2005-09-03
forum: Hardware &amp; Laptops
---

### Post by derheinrich on 2005-09-03
Hi!
I've read all the posts to this topic but just can't find an answer. 
I've just installed Ubuntu on my linux-box which used to be running Debian woody. 
After installing everything on my first harddisk I connected my second disk as a primary slave drive (I had disconnected it just in case ubuntu wanted to partition it for me). Trying to mount the partition hdb2 with 
 mount -text3 /dev/hdb2 /mnt/disk2 

gives me a:  mount: /dev/hdb2 already mounted or /disk2 busy error

My mount-version is 2.12b
my /etc/fstab is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none         swap    sw              0       0
/dev/hdb2       /mnt/disk2 ext3    rw,user,auto    0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

my mtab:

/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
/dev /.dev unknown rw,bind 0 0
none /dev tmpfs rw,size=5M,mode=0755 0 0
usbfs /proc/bus/usb usbfs rw 0 0

fdisk -l:

Disk /dev/hdb: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         129     1036161   82  Linux swap / Solaris
/dev/hdb2             130       14595   116198145   83  Linux

I am wondering if it has anything to do with the sysfs since I can find the disk under /sys/block/hdb/hdb2 and that the kernel is thinking that it is already in use. If yes-> what do I need to do to turn it off? 

The disk was working perfectly this morning in the same configuration, only under Debian Woody... 

Thanks!

---

### Post by derheinrich on 2005-09-03
Found the problem:

I had added a deb-source from debian because I needed a ruby-file which I thought I could not find under ubuntu (until I understood what multiverse means :wink: ) . Afterwards I let the system update itself without actually looking at what was being updated. The system also updated the kernel from 2.6.10 to 2.6.12 which I thought wouldn't be so tragic but this must have been the problem. After a fresh install of ubuntu *without* using the deb-source from debian the mount-command works without any problems.

Ubuntu really rocks! I've never had a system up and running that fast before.

---

