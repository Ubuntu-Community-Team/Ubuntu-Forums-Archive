---
title: "[SOLVED] How do you find UUID?"
date: 2007-01-30
forum: Hardware &amp; Laptops
---

### Post by montgoss on 2007-01-30
I know I'm supposed to edit /etc/fstab in order to get a partition automatically mounted at startup.  But all the other partitions already there have the first parameter as UUID=<something>.  How do I find out what to put there for these currently unmounted partitions?

---

### Post by glabouni on 2007-01-30
```
blkid 
```
or
```
ls /dev/disk/by-uuid
```

---

### Post by tommcd on 2007-01-30
fstab will work with or without UUIDs. The UUIDs were added so that if you switched hard drives around or changed your partitioning scheme the fstab could still find them. Another way to get UUIDs (so I've read, have not tried it) is:

sudo vol_id -u <partition>
See:
[http://ubuntuforums.org/showthread.php?t=286758](http://ubuntuforums.org/showthread.php?t=286758)
[http://www.ubuntuforums.org/showthread.php?&t=283131](http://www.ubuntuforums.org/showthread.php?&t=283131)

---

### Post by Man_Beach on 2007-01-30
So I don't _have_ to use the UUID in fstab? I can use /dev/hda8 or whatever instead?

---

### Post by hal10000 on 2007-01-30
yes you can; you can also use them in your /boot/grub/menu.lst if you like.

---

### Post by jameshoo on 2008-05-05
> **hal10000 said:**
> yes you can; you can also use them in your /boot/grub/menu.lst if you like.

watch out where the huskies go
and don't you eat that yellow snow (Zappa)


:lolflag:
[http://ubuntuforums.org/images/smilies/smiley-faces-75.gif](http://ubuntuforums.org/images/smilies/smiley-faces-75.gif)

I like Zappa. I've a stroke and perhap of Zappa. Them days were cuaght of all the days of those. Thanks for those of though of thoughts...  Jim

---

### Post by warp4ever on 2008-06-16
How about this then ?

root@server1:~# blkid
/dev/sda1: UUID="ed5b5804-bf8c-4a4c-a576-e6b31108eb28" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="e97c27fe-0000-0000-0000-00000000cc12" TYPE="jfs" 
/dev/sdb6: UUID="e97c27fe-0000-0000-0000-00000000cc12" TYPE="jfs" 
/dev/sdb7: UUID="e97c27fe-0000-0000-0000-00000000cc12" TYPE="jfs" 
/dev/sdb8: UUID="ab410eb4-2c5f-4dec-9276-910ce64c8e23" TYPE="jfs" 
/dev/sda5: TYPE="swap" UUID="742b5801-411e-4396-813b-a5b809b1f275" 
/dev/sdc1: LABEL="frama" UUID="8756178d-d7c8-4168-88ee-24b878048120" TYPE="ext3"

---

### Post by Krupski on 2008-07-01
> **glabouni said:**
> ```
blkid 
```
or
```
ls /dev/disk/by-uuid
```

Hi!

I have a network storage machine made up like this:

* Ubuntu 8.04 Server
* A 4.0 GB Compact Flash Drive to hold the OS
* Two 1 TB hard drives as RAID 1 mirror storage (created using MDADM and shared on the network via SAMBA).

There is not one byte of Linux on the hard drives... it's all on the CF card.

Anyway, I have been using UUID's in my FSTAB and GRUB files because /dev/sda /dev/sdb and /dev/sdc don't always stay the same names and if they decide to switcheroo, the box won't boot.

Now, I have been making periodic backups of my CF flash card just in case I mess things up - I can go back to a "last known good" system.

I have been doing this by physically pulling the card and using WINIMAGE to make an image of it.

I have since tried (successfully) to use DD to copy the drive to a file which I can then copy from the SAMBA share to my local machine (i.e. no more pulling the card out).

What I would like to know is, can I reference the boot drive (using DD) with a UUID rather than /dev/sda?

Here's the line I've been using to image the CF card:

```
dd if=/dev/sda of=/home/shared/linux-backup.img bs=1M count=4096
```

Can I replace "/dev/sda" with a UUID?

I can find the UUID for partitions like /dev/sda1, etc... but not for the DRIVE itself (i.e /dev/sda).

Thanks in advance for any help!

-- Roger

---

### Post by Krupski on 2008-07-01
> **Man_Beach said:**
> So I don't _have_ to use the UUID in fstab? I can use /dev/hda8 or whatever instead?

I would heartily suggest USING the UUID format since it is device name independent and I've found sometimes drives swap names all by themselves and, if this happens, your machine won't boot.

UUID *always* works.

---

