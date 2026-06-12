---
title: "can't automount DVD , only manual mount"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by 9047boy on 2008-02-05
Hi .

I am having a problem with automounting of some of my DVDs .
I cam mount them manually without problems using :

goatboy@goatboy:~$ sudo mount -t iso9660 /dev/scd0 /media/cdrom0
[sudo] password for goatboy:
mount: block device /dev/scd0 is write-protected, mounting read-only
goatboy@goatboy:~$ 

but when i try to automount it i get the following error message :

[[IMG]http://img220.imageshack.us/img220/2527/screenshotgnomemountfp1.th.png[/IMG]](http://img220.imageshack.us/my.php?image=screenshotgnomemountfp1.png)

I tried following the advice from this post :[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=510748](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=510748)
but nothing worked .

My fstab file entry looks like this :

/dev/scd0       /media/cdrom0   auto user,noauto,exec 0       0

The OS is Ubuntu Studio 7.10 .

Thanks .

---

### Post by yabbadabbadont on 2008-02-05
Try changing the fstab entry from
```
/dev/scd0 /media/cdrom0 auto user,noauto,exec 0 0
```
to
```
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
```

---

### Post by Yellow Pasque on 2008-02-05
> **9047boy said:**
> 
My fstab file entry looks like this :

/dev/scd0       /media/cdrom0   auto user,noauto,exec 0       0

Try changing 'noauto' to 'auto'?

---

### Post by 9047boy on 2008-02-05
To yabbadabbadont , 

the udf,iso9660 was in my fstab by default and the thing is that this is a fresh install with full updates .

Regarding the noauto/auto flag , isn't that supposed to tell if the drive should be or not be mounted at boot time ? :-/ . I will try it anyway .

Thanks for the advice :)

Another thing i noticed is that if i leave the DVD in the drive and reboot it will be mounted automatically and i will be able to read it, but if i unmount it and then try automount-ing it again it won't work .

---

### Post by yabbadabbadont on 2008-02-05
Are there any error messages in your dmesg output?

(Run, "dmesg", in a terminal window, if you didn't already know that.)

((I'm guessing you did, but better safe than sorry.  ;)))

---

### Post by 9047boy on 2008-02-05
no , i get no errors from dmesg . not even an entry .
the only entries i get are only after i manually mount the DVD :

goatboy@goatboy:~$ mount /media/cdrom0
mount: block device /dev/scd0 is write-protected, mounting read-only
goatboy@goatboy:~$ 

and this gives in dmesg :

[  244.253276] ISO 9660 Extensions: Microsoft Joliet Level 3
[  244.254677] ISOFS: changing to secondary root

---

### Post by Yellow Pasque on 2008-02-05
I'm sorry, can you clarify for me: Are you saying that the DVD still is not auto-mounting when you stick it in the dvd drive and gives you no indication that you inserted a disc when you look at dmesg?

---

### Post by 9047boy on 2008-02-05
Yes , exactly . The only thing i get is the message from the image i posted : There is probably no media in the drive .

---

### Post by cdtech on 2008-02-05
How old is the drive?

Dirty laser perhaps?

The drive starts up (wants to auto mount), you get the message, but it can't see the disk.

---

### Post by 9047boy on 2008-02-05
hmmmm . . . about 6 or 7 months old

---

### Post by cdtech on 2008-02-05
> **9047boy said:**
> some of my DVDs

I say that because of your post.  If it's with some, clean the laser.  Just shoot some air in there.

---

### Post by 9047boy on 2008-02-05
i will try that too . . .but the thing is that i can mount the dvds manually and read/copy from them with no problems :-??

---

### Post by cdtech on 2008-02-05
I've also heard that hal (Hardware abstraction layer) could cause this.  Some fixes would be to upgrade hal, or uninstall / reinstall.  Do you have any other problems with, say, USB devices?

---

