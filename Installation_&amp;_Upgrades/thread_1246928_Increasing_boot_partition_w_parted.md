---
title: "Increasing /boot partition w/ parted"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by claus on 2009-08-22
Hi,

when trying to install the recent updates on 9.04, I got a notification saying that my /boot partition is too small. My question: How can I increase this partition (/sda1) without losing any content in the other partitions?

My fstab looks as follows:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=f4ac0e0c-931a-415b-baa5-b7fb9dc9df21 /               reiserfs relatime        0       1
# /dev/sda1
UUID=baabca30-5578-40bc-9011-a9cd416d4507 /boot           reiserfs notail,relatime 0       2
# /dev/sda8
UUID=70860176-1bb3-4e2c-bb41-7cf72dc9ab3d /home           reiserfs relatime        0       2
# /dev/sda7
UUID=ba38ba1d-d9a0-4b32-bc71-4c1d51b218b0 /usr            reiserfs relatime        0       2
# /dev/sda6
UUID=5947412b-e498-48c8-b7f8-62eccf2749e2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

parted listing:

> Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  98.7MB  98.7MB  primary   reiserfs     boot 
 2      98.7MB  33.8GB  33.7GB  extended                    
 5      98.7MB  5100MB  5001MB  logical   reiserfs          
 6      5100MB  6103MB  1003MB  logical   linux-swap        
 7      6103MB  16.1GB  10.0GB  logical   reiserfs          
 8      16.1GB  33.8GB  17.7GB  logical   reiserfs    

Any help highly appreciated,

Claus

---

### Post by drs305 on 2009-08-22
Since your boot partition is a primary partition and the rest are all logical parttions, you will have to do this in stages.

If you want to keep the /boot partition as a primary partition, the easiest way would be to:
1. Backup important data.
2. Shrink sda5 as much as you want to expand sda1. (Leave the free space at the front of the partition).
3. Shrink the expanded partition.
4. Expand sda1

I posted a thread on resizing the / partition. It doesn't apply specifically to your case but most of the principals are the same - just think /boot where it says 'windows'.
[http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")

Alternatively, if you have a lot of older kernels still lurking about in your /boot partition you could try to remove them to see if you have enough space, although a 98MB /boot partition could trouble you again in the future.

---

