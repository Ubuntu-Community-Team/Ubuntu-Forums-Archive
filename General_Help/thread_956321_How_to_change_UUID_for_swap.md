---
title: "How to change UUID for swap"
date: 2008-10-23
forum: General Help
---

### Post by Greeny2008 on 2008-10-23
Hi.

The first time i have seen Linux was 3 days so im as inexperienced as it gets when it comes to using the terminal.

I initially made the swap partition (sda6) to small so i resized it using gparted live. Now the swap doesnt turn on when ever i restart. I have to swap on manually via the gparted GUI.

From much google searching I think the problem is that the UUID has changed.

samuel@samuel-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=473111dc-4595-444a-8a64-710ec798fa29 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=25817e22-3e99-4307-ae13-3fa6a4765e76 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


samuel@samuel-laptop:~$ sudo blkid
/dev/sda1: UUID="E61000CA1000A421" TYPE="ntfs" 
/dev/sda5: UUID="473111dc-4595-444a-8a64-710ec798fa29" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="5c828979-e11f-48c0-8e5c-f7f00d99d7b1" 

I have been unable to change it.
Can someone please tell me 'exactly' what to type in the terminal to change the UUID from UUID=25817e22-3e99-4307-ae13-3fa6a4765e76 toUUID="5c828979-e11f-48c0-8e5c-f7f00d99d7b1" 

Thanks

---

### Post by geirha on 2008-10-23
You edit /etc/fstab and change the UUID there to what blkid says

```
gksudo gedit /etc/fstab
```

EDIT: Sorry, you are using xubuntu, I don't know what GUI editors are installed by default in xubuntu. You can use nano though:
```
sudo nano /etc/fstab
```

When you're done editing, hit ^X (meaning Ctrl+X), y to save and hit enter to save at /etc/fstab.

---

### Post by Greeny2008 on 2008-10-23
Your a dead set legend!
That nano thing worked!

Cheers

---

