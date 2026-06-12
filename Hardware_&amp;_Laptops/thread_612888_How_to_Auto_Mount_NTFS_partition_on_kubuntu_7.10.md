---
title: "How to Auto Mount NTFS partition on kubuntu 7.10"
date: 2007-11-14
forum: Hardware &amp; Laptops
---

### Post by aakashk on 2007-11-14
Hello All,


I am Aakash from India. Am new to Ubuntu (Kubuntu) 7.10 linux.
Initially after installing ubuntu, I didn't face any problem of auto mount. I used to log in as  aakash and could see 2 ntfs partition. sda1 and sda2.
But, ever since I formatted both drive sda1 and sda2 and re-install windows xp home edition on sda1 (C:), previously windows xp prof was installed on sda5 (D:), I can't see the 2 ntfs partition at start up. I have to click on Places and Computer and there I see those 2 ntfs partition but not mounted. I have to double click and put it the root password to enable it once, after which it doesn't ask for any password untill I shut down the system.

So my question to all is how can I auto mount both the partition at boot itself so that once I logged in, can access it.

One more thing I notice is when I set the wallpaper from sda1 and restart the pc, it goes off. I guess its because of the disk is not mounted automatically at boot and hence it doesn't show the wallpaper which was set from sda1.

I am providing you all details of /etc/fstab.

I would appreciate if someone could assist/help me out of this.


Thanks,
Aakash


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=f3314244-0589-4c80-8abe-08ce641da96b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=EE54996C549937F3 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=56AC57C5AC579DF5 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=26a0abd6-c43d-407e-a258-c75719e35ad4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by bakeneko on 2007-11-14
First: always backup important system files like /etc/fstab before changing them.

Reformatting your drives will cause them to be assigned a new UUID.  You can find out the drives' new UUID by entering (at the console):
```
$ sudo vol_id -u <partition>
```
And then update your fstab accordingly.

---

### Post by aakashk on 2007-11-14
Hello Bakeneko,

Thanks for the reply. This is what I have done so far.

I have taken the backup of /etc/fstab to /home/aakash/documents

and then started the terminal window and typed the following. Both the drives are already mounted. I just want to know how can I auto mout during system boot up so as after I log into the system as aakash, I should be able to access the drives

aakash@aakash-laptop:~$ sudo vol
vol_id   volname  
aakash@aakash-laptop:~$ sudo vol_id -u sda1
[sudo] password for aakash:
sda1: error opening volume
aakash@aakash-laptop:~$ sudo vol_id -u sda5
sda5: error opening volume
aakash@aakash-laptop:~$ 

Thanks,
Aakash

---

### Post by l2thet on 2007-11-14
Looks like a little bit of syntax was missing there, this should give you what your looking for

sudo vol_id -u /dev/sda1

sudo vol_id -u /dev/sda5

---

### Post by aakashk on 2007-11-14
Thanks to both of you

bakeneko and l2thet  

Both of my problem got solved.
1st the 2 ntfs drives get automatically mount at startup and
2nd the wallpapers remain even after rebooting the system

You guys ROCK!!!

Cheers!
Aakash

---

