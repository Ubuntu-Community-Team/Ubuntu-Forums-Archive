---
title: "Hard Drive Recovery (force mount?)"
date: 2008-09-11
forum: Hardware
---

### Post by wissemeier05 on 2008-09-11
Good Evening,

A friend of mine crashed their windows box and asked if I could recover their files before they nuked the hard drive and started fresh.

So she brought the tower over....it was a dell...... I pulled the hard drive and hooked it up to my Linux (8.04) laptop via a hard drive key. 


hard drive key
[http://www.newegg.com/Product/Product.aspx?Item=N82E16812161002](http://www.newegg.com/Product/Product.aspx?Item=N82E16812161002)


I have recovered files in the past just plug in and read it like a big flash drive.  This time the hard drive will not "mount" and I cannot access it.  Are there any tricks for "force" mounting an external drive?

Here is the error I am getting. 
[IMG]http://img374.imageshack.us/img374/1333/screenshot1kq7.png[/IMG]

TIA
Dan :confused:

---

### Post by srt4play on 2008-09-11
```
sudo ntfs-3g /dev/sd? /media/? -o force
```

Replace the question marks with correct drive device name and mountpoint.

---

### Post by wissemeier05 on 2008-09-11
Thanks for the reply,  How do i determine what the mount point is?
(i am still kinda new at all of this)

Thanks,
Dan

---

### Post by srt4play on 2008-09-11
> **wissemeier05 said:**
> Thanks for the reply,  How do i determine what the mount point is?
(i am still kinda new at all of this)

Thanks,
Dan

It's whatever you want it to be. For example, you could create a directory /media/external

```
sudo mkdir /media/external
```

So the command becomes:

```
sudo ntfs-3g /dev/sd? /media/external -o force
```

---

### Post by wissemeier05 on 2008-09-11
[IMG]http://img128.imageshack.us/img128/5389/screenshot2an5.png[/IMG]
 

dan@dan-laptop:~$ sudo fdisk -l
[sudo] password for dan: 

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4d08e236

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3916    31455238+   7  HPFS/NTFS
/dev/sda2            3917       24321   163903162+   f  W95 Ext'd (LBA)
/dev/sda5            3917        7180    26218048+  83  Linux
/dev/sda6            7181        7442     2104483+  82  Linux swap / Solaris
/dev/sda7            7443        7460      144553+   7  HPFS/NTFS
/dev/sda8            7461       24321   135435951    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf52bcf0e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1           5       40131   de  Dell Utility
/dev/sdc2   *           6        9725    78075900    7  HPFS/NTFS
dan@dan-laptop:~$



so then after I run 
"sudo mkdir /media/external"

I could run

sudo ntfs-3g /dev/sd? /media/external -o force

and instead of a "?" I would put "c2"

---

### Post by wissemeier05 on 2008-09-11
It worked !  Thanks a Ton!

Dan

---

### Post by fuzzywigg on 2008-11-26
This post was GREAT!!  It really got me out of a pinch.  Note to self, Windows does not play nice with others.

Great work Ubuntu community :-)

---

### Post by josesalinasc on 2009-08-30
hello, i have the same problem only my hard drive is in EXT3 format
I tried to change  "sudo [COLOR="Red"]ntfs[/COLOR]-3g /dev/sd? /media/external -o force" to EXT3 and had no luck

this may need a totally diferent code

thanks

---

### Post by bumanie on 2009-08-30
Educated guess would be that you need to remove ntfs-3g, not just ntfs as ntfs-3g is a package that allows read/write to ntfs filesystems. Put ext3 where ntfs-3g is. Not sure why you can't mount ext3, unless the filesystem is very damaged, if so:
You could try photorec which is part of testdisk. Despite the name, photorec recovers much more than photos - I think there are 100+ file types it can recover. It is filesystem independent, so it works even if the filesystem is wrecked. It can be run off a live cd sudo apt-get install testdisk, then in terminal sudo photorec to start the program. Alternatively, go [here]("http://www.cgsecurity.org/wiki/TestDisk") to download a specific live cd of testdisk or a usb pendrive version. There are also tutorials on the above site. Good luck.

---

### Post by nick8539 on 2009-08-30
Hi hopefully someone can help me....

when I try to put in this command it says

sudo: ntfs-3g: commad not found

I'm fairly new at this but i am trying to recover data from a hard drive..

I put 


sudo ntfs-3g /dev/sda3/ media/external -o force

---

### Post by Bridget Fond on 2009-09-30
Yeah i works but sometimes it does not work and says command not found.i got the same problem but i was very much interested in recovering my data back then i simply use a Linux recovery tool helps in recovering my data back.The tool **Stellar Phoenix Linux Data Recovery software** is quite efficient and helpful in recovering data from hard drive when it does not mound and couldn't find valid file system superblock.The software can recover data incase running fsck command on mounted file system fails.

---

### Post by dmccull on 2010-03-12
> **srt4play said:**
> ```
sudo ntfs-3g /dev/sd? /media/? -o force
```Replace the question marks with correct drive device name and mountpoint.


I have done this and get the attached error,does this mean I am stuffed? I am running ubuntu 9.10 from a usb flash drive as my Windows Vista hard drive has tanked - it is still detecting fine but ubuntu refuses to mount it even when I use the force command.

Thanks... 

[IMG]http://ubuntuforums.org/home/ubuntu/desktop/screen.png[/IMG]

---

### Post by dmccull on 2010-03-13
Bump... Would really like some feedback on this one guys... even if it is confirming that I've lost everything - at least then I can begin the mourning process :(

---

### Post by viper250 on 2010-03-13
aside from caine linux which is a forensic distro
you can use puppy linux to recover files from a tanked drive 
the only drives I couldn't recover from were drives that would not even spin up (burned controller cards)((I don't have the facilities or equipment to do that yet)

---

