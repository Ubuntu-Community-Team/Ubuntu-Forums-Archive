---
title: "Unable to mount USB keys"
date: 2006-09-21
forum: Hardware &amp; Laptops
---

### Post by brightnemo on 2006-09-21
Hi everybody!

I got a problem with a Sony USB micro vault of 1 GB. I bought the piece in a shop around town, over there the seller plugged the key in his laptop to show me the right capacity of the key (i live in China, quite common procedure when you buy something). Everything was fine over there.

At home, I was unable to mount the key in Ubuntu or in windows. In the redmond system the key was able to freeze completely explorer, until I physically plugged of the key. In my dapper when I plug the key the system try to mount the device, but after several minutes it gave up with this message:

Could not mount device.
The reported error was:
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab

I'm afraid the key is just broken, but there is a way to know for sure? I want to give it a try before come back to the seller in my -yelling mode- on!

thanks

---

### Post by John.Michael.Kane on 2006-09-21
Is the key formated with a diffrent filesystem?

---

### Post by brightnemo on 2006-09-21
I'm trying right now to change filesystem with mkfs


```
nemo@Aleph:~$ sudo mkfs.ext3 -cv /dev/sda1
Password:
mke2fs 1.38 (30-Jun-2005)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
134217728 inodes, 268434093 blocks
13421704 blocks (5.00%) reserved for the super user
First data block=0
8192 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
        102400000, 214990848

Writing inode tables:  
```

It's quite slow, I'm waiting to see if everything goes ok...

Thanks

---

