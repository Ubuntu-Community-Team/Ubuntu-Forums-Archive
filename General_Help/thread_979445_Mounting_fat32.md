---
title: "Mounting fat32"
date: 2008-11-10
forum: General Help
---

### Post by bobd72 on 2008-11-10
Hello,
Perhaps someone can help.  
I upgraded from Kubuntu 8.04 to 8.10 and my fstab entry to mount vfat hard drive at boot no longer works.
 
The D$ drive is called WINDATA and I can see it in Dolphin but it is not mounted at startup.  I can mount it by clicking and then entering the root password, but it creates a new folder called /media/WINDATA-1 and mounts it there.

I have a shared folder at /media/WINDATA where it is intended that the drive is mounted.
My fstab entry is:
//192.168.72.1/D$ /media/WINDATA cifs rw,credentials=/home/bob/windata 0    0

and credentials file:
username=share
password=myshare
domain=mydomain
uid=1000
gid=1000

This setup worked perfectly in 8.04

Thanks

---

### Post by bobd72 on 2008-11-11
> **bobd72 said:**
> Hello,
Perhaps someone can help.  
I upgraded from Kubuntu 8.04 to 8.10 and my fstab entry to mount vfat hard drive at boot no longer works.
 
The D$ drive is called WINDATA and I can see it in Dolphin but it is not mounted at startup.  I can mount it by clicking and then entering the root password, but it creates a new folder called /media/WINDATA-1 and mounts it there.

I have a shared folder at /media/WINDATA where it is intended that the drive is mounted.
My fstab entry is:
//192.168.72.1/D$ /media/WINDATA cifs rw,credentials=/home/bob/windata 0    0

and credentials file:
username=share
password=myshare
domain=mydomain
uid=1000
gid=1000

This setup worked perfectly in 8.04

Thanks

In hunting around to try to resolve this I find:

bob@Comp1:/$ sudo mount /media/WINDATA
mount: special device /dev/hdb1 does not exist

My fstab contains the line:
/dev/hdb1    /media/WINDATA vfat user,iocharset=utf8,umask=000  0    0

How come I can't mount it?

---

### Post by dmizer on 2008-11-12
> **bobd72 said:**
> In hunting around to try to resolve this I find:

bob@Comp1:/$ sudo mount /media/WINDATA
mount: special device /dev/hdb1 does not exist

My fstab contains the line:
/dev/hdb1    /media/WINDATA vfat user,iocharset=utf8,umask=000  0    0

How come I can't mount it?

Hello,

You posted in a thread is concerning how to mount network shares with CIFS, not with mounting local partitions. I've split out your posts into a new thread here in the General help section.

See if the Ubuntu wiki has what you need to know: [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions), if you need help with it, please feel free to ask. Thank you!

---

### Post by bobd72 on 2008-11-12
Oh dear - my apologies.  Back to the drawing board :-( 
Thanks

---

