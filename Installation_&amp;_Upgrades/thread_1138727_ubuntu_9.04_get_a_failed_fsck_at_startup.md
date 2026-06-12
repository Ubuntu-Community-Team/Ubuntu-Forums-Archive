---
title: "ubuntu 9.04 get a failed fsck at startup"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by calin_ionut on 2009-04-26
I just installed the new Ubuntu 9.04. Everything works fine with one exception....when it boots up i get get a failed fsck and i have to do it manually. This is happening every time i boot up ubuntu. Here is the log /var/log/fsck/checkfs:

```

Log of fsck -C3 -R -A -a 
Sun Apr 26 22:13:56 2009

fsck 1.41.4 (27-Jan-2009)
fsck.ext4: Unable to resolve 'UUID=fd501772-0cb3-4933-b69b-22933c644162'

/dev/sda8: clean, 9846/8609792 files, 711446/34411222 blocks
fsck died with exit status 8

Sun Apr 26 22:13:56 2009
----------------

``` 

It gives me a shell, i do it manualy and then resume to boot up. What can i do to fix this issue? :confused:

---

### Post by cbeneke on 2009-04-27
I think I'm having the same problem.  I have an 8gb sd card that I put my /home directory on, but I get the message fsck.ext4: Unable to resolve 'UUID=......"

I checked the UUID of my SD card using ls -l /dev/disk/by-uuid and the UUID for sdb1 (my SD card) matches the second line of my fstab file.

If this is a different problem from the OP, I apologize.  They seem similar enough to be mentioned.

Also, I'm using 9.04 Netbook Remix, although I have also tried with 9.04 Desktop edition and have had the same experience.  Same issue regardless of using ext3 or ext4.

I'm actually wondering if this is a bug because it happens the first time I boot after a fresh install.  During the install I specify to manually define the partitions.  I put / on the built in SSD and /home on the SD card.  I did the exact same thing with 8.10 with no issues, so I can only assume that something broke in the new version.

---

### Post by calin_ionut on 2009-04-27
I guess it`s a BUG :( I will try to resolve this problem somehow because it`s very annoying, every time i boot up i have to do it manually.


Cheers!

---

### Post by cbeneke on 2009-04-27
I agree that this seems like a bug because the same exact setup worked in 8.10 and 8.04.  Once I press ctrl+D, the system boots and runs just fine, but I'm itching to take advantage of the decreased boot time of Jaunty + ext4 on my SSD and this kind of gets in the way.

---

### Post by calin_ionut on 2009-05-02
Somehow i fixed this issue! cbeneke if you still have this issue try to compare the uuid values from the command 

```

blkid

``` 

and 

```

cat /etc/fstab

```

My problem was with the external usb hdd, which that value uuid from the /var/log/fsck/checkfs:

```

sck 1.41.4 (27-Jan-2009)
fsck.ext4: Unable to resolve 'UUID=fd501772-0cb3-4933-b69b-22933c644162'

```

was to that hdd external which is it in /etc/fstab 

```

# /MyStuff was on /dev/sdb1 during installation
UUID=fd501772-0cb3-4933-b69b-22933c644162 /MyStuff        ext4    relatime        0       2

```

This is strange, the command blkid doesn`t show me the uuid for the external drive, which i want to compare with the uuid from the fstab. 

So what i did i comment that entry from fstab and now boot just fine, and it mount the external drive automatically on desktop. 

Cheers!

---

### Post by hihihi on 2009-05-15
> **calin_ionut said:**
> 
...
This is strange, the command blkid doesn`t show me the uuid for the external drive, which i want to compare with the uuid from the fstab. 
...


try 
```
$ sudo vol_id /dev/***disk_to_check_id***
```
this gives you all uuid-info you need to work on your fstab

if I want to know uuid from sda6 then i do:
```
$ sudo vol_id /dev/**sda6**
```
which gives me:
```
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=29dd8550-49a7-4b59-9780-c213bb8da0bd
ID_FS_UUID_ENC=29dd8550-49a7-4b59-9780-c213bb8da0bd
ID_FS_LABEL=
ID_FS_LABEL_ENC=
```


good luck

---

### Post by kpkeerthi on 2009-05-15
> **calin_ionut said:**
> 
This is strange, the command blkid doesn`t show me the uuid for the external drive, which i want to compare with the uuid from the fstab. 

You should use **sudo blkid**
The UUID will change if you alter the partitions.

---

