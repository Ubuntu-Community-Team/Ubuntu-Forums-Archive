---
title: "Ubuntu won't mount dvd's"
date: 2010-03-29
forum: Hardware
---

### Post by hisotaso on 2010-03-29
I'm running Ubuntu Karmic, and for some reason it wont mount dvd's. I started having problems when I upgraded to Karmic when it was released. I am able to mount cds jsut fine, just no dvds. A friend gave me another drive to try, and no dice. So i have the disc for maple 13 that I need for school, i pop it in, nothing. I put the dvd in my wifes machine and it works just fine. So today I put her drive in my machine and still, it wont mount dvds. It doesn't matter if they are store bought, blank, burned, etc, it just wont mount any dvds. Here is a copy of my fstab:

proc /proc proc defaults 0 0

# Entry for /dev/sda1 :
UUID=08868ad9-84f4-4b6c-a762-a661e8455551 / ext4 errors=remount-ro 0 1

# Entry for /dev/sda5 :
UUID=245e0750-26a5-4389-b1e1-432f6db85a99 none swap sw 0 0

/dev/scd0 /media/cdrom0 iso9660 ro,user,noauto  0       0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sdb1 /media/sdb1 ntfs-3g defaults,locale=en_CA.UTF-8 0 0
/dev/sdc1 /media/SDcard vfat uid=1000,umask=007,gid=1000,users,user 0 0

also, when type dmesg | tail in terminal i get:


[   73.769386]  CIFS VFS: Unexpected lookup error -26
[   73.771107]  CIFS VFS: Unexpected lookup error -26
[   73.773246]  CIFS VFS: Unexpected lookup error -26
[   73.774969]  CIFS VFS: Unexpected lookup error -26
[   73.776688]  CIFS VFS: Unexpected lookup error -26
[   73.822368]  CIFS VFS: Unexpected lookup error -26
[   73.847360]  CIFS VFS: Unexpected lookup error -26
[   73.894419]  CIFS VFS: Unexpected lookup error -26
[   74.045157]  CIFS VFS: Unexpected lookup error -26
[   75.344176]  CIFS VFS: Unexpected lookup error -26
 
Any ideas?

---

