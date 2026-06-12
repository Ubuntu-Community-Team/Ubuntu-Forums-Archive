---
title: "Sharing files between XP and Ubuntu"
date: 2008-11-22
forum: General Help
---

### Post by TheMyself on 2008-11-22
Hello everybody

My hard disc has two partitions, one for XP and the other for Ubuntu. I've installed a software which allows me to read and write on Ubuntu's partition from XP but from Ubuntu I can't write on XP partition when it's hibernated.

So I decided to take a third partition out of Ubuntu's (which has a lot of empty space) to put the shared documents in. (This is also motivated by a frightful "unclean shotdown".) But I can't do that in Gparted. Apparently I have to unmount Ubuntu's partition first which doesn't seem to be possible. Also XP disc manager regards Ubuntu partition as empty. Is there anything that I can do?

Thank you

---

### Post by thomas228 on 2008-11-22
> **TheMyself said:**
> Hello everybody

My hard disc has two partitions, one for XP and the other for Ubuntu. I've installed a software which allows me to read and write on Ubuntu's partition from XP but from Ubuntu I can't write on XP partition when it's hibernated.

So I decided to take a third partition out of Ubuntu's (which has a lot of empty space) to put the shared documents in. (This is also motivated by a frightful "unclean shotdown".) But I can't do that in Gparted. Apparently I have to unmount Ubuntu's partition first which doesn't seem to be possible. Also XP disc manager regards Ubuntu partition as empty. Is there anything that I can do?

Thank you

Have you used the Ubuntu live cd to accomplish creating a new partition?
Read this all the way through for some good hints
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=2](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=2)

It helped me a lot with my dual boot on separate partitions

Let me know if it helps and good luck

Tom

---

### Post by ywilliams12345 on 2008-11-22
Can you give a pointer to how you manage to read/write
Ubuntu partition from XP?
thanks




> **TheMyself said:**
> Hello everybody

My hard disc has two partitions, one for XP and the other for Ubuntu. I've installed a software which allows me to read and write on Ubuntu's partition from XP but from Ubuntu I can't write on XP partition when it's hibernated.

So I decided to take a third partition out of Ubuntu's (which has a lot of empty space) to put the shared documents in. (This is also motivated by a frightful "unclean shotdown".) But I can't do that in Gparted. Apparently I have to unmount Ubuntu's partition first which doesn't seem to be possible. Also XP disc manager regards Ubuntu partition as empty. Is there anything that I can do?

Thank you

---

### Post by erwall on 2008-11-23
> **ywilliams12345 said:**
> Can you give a pointer to how you manage to read/write
Ubuntu partition from XP?
thanks
[http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by TeXtonyx on 2008-11-23
[http://www.diskinternals.com/linux-reader/screenshots.shtml](http://www.diskinternals.com/linux-reader/screenshots.shtml)

At first glance fs-driver seems better because you can write rather
than just read from Windows. But I've read about complaints that
there system degraded after awhile of making writes to Linux from
Windows. LinuxReader allows you to save files from the Ubuntu
partition and read them in Windows, making changes, but not write
the changed file back to Linux. 

Linux has the ntfs-3g driver which lets you mount windows in fstab
and you can copy a changed file back to Ubuntu from the mounted
Windows partition, if you want. You can write to the Windows partition
from the Ubuntu partition because of the ntfs-3g driver. Also
install ntfs3g-config and run it. You can find details in Search.

---

### Post by TheMyself on 2008-11-23
Thank you. I'll use the Ubuntu live CD (I don't have it around now).
I use Ext2 IFS to write on Ubuntu partition but I don't have to do that once I get a new partition.

---

### Post by TheMyself on 2008-11-24
I created a new NTFS partition but now I observe that it is "mounted" somewhere inside my Ubuntu partition. Apparently Ubuntu copies the contents of that partition into its own partition. Is this true? And doesn't this reduce speed?

---

### Post by Archmage on 2008-11-24
> **TheMyself said:**
> I created a new NTFS partition but now I observe that it is "mounted" somewhere inside my Ubuntu partition. Apparently Ubuntu copies the contents of that partition into its own partition. Is this true? And doesn't this reduce speed?

Nope. It is just mounted there. In Linux you can mount harddrives whereever you want. E.g. have your second harddrive under /home/themyself/music and the third under /home/themself/music/hardcore.

---

