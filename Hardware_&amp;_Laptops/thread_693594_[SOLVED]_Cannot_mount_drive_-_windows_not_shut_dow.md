---
title: "[SOLVED] Cannot mount drive - windows not shut down safely"
date: 2008-02-11
forum: Hardware &amp; Laptops
---

### Post by Gleep on 2008-02-11
My windows installation has broken for fun... it just blue screens whenever I start it up... no idea why, it's a little annoying but I thought I'd just backup everything onto ubuntu and reformat, since I don't use windows that much anyway and won't miss much.

However then we have the problem that I can't mount it... I get the error that it cannot be mounted because it wasn't shut down properly...

Oddly, one day it decided to mount... the only thing I could think of was that it had fixed itself somehow by magic, tried to boot into windows and it still bluescreened... meaning it didnt get shut down properly AGAIN.

Then I worked out that it was probably in fact just that it had done the automatic every thirty boots disk check.

I have tried running sudo touch /forcefsck and then restarting. But when I've restarted it just says it cannot mount sda1 when I try to mount it..


Running fdisk -l gives me this

verena@verena-desktop:~$ sudo fdisk -l
[sudo] password for verena:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00076d6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19269   154778211   83  Linux
/dev/sda2           19270       19457     1510110    5  Extended
/dev/sda5           19270       19457     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xab98ab98

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14945   120045681    7  HPFS/NTFS


I might not know what I'm talking about but I always thought that sdb meant it was a sata drive and hda meant IDE? I know for a fact both my hard drives are IDE so I'm not sure why it's saying sda in that case... but as I said that's just something I heard I'm no expert by any means.

I'm not sure how clear I've been here, but if anyone knows what I need to do, any help would be greatly appreciated.

---

### Post by Yellow Pasque on 2008-02-11
I believe you have to do a force mount then.
```
sudo mount -t ntfs-3g /dev/sdb1 <directory to mount to> -o force
```

---

### Post by Gleep on 2008-02-11
> **Temüjin said:**
> I believe you have to do a force mount then.
```
sudo mount -t ntfs-3g /dev/sdb1 <directory to mount to> -o force
```I'm too much of a n00b to know where to mount to :(

---

### Post by Salpiche on 2008-02-11
try making a directory on your home directory
 ```
sudo mkdir /home/your-user-name/whatever-you-want-to-name-it 
```

then, just to make sure that you can write to it (if you need to write)
```
sudo chmod 0777 /home/your-user-name/whatever-you-want-to-name-it 
```

then do (as perTemüjin)
```
sudo mount -t ntfs-3g /dev/sdb1 /home/your-user-name/whatever-you-want-to-name-i -o force
```

hope we helped

---

### Post by Gleep on 2008-02-11
Thanks that worked. I have backed everything up now, but when I go to reinstall windows, it says that it wants to format a partition on my ubuntu hard drive... this I obviously don't want, especially since I was asking it to specifically install it on the drive with windows already on it...

I don't know why it's doing this but I don't know how to get around this, any ideas? Should I make a new thread? 
:(

---

### Post by Salpiche on 2008-02-11
> **Gleep said:**
> Thanks that worked. I have backed everything up now, but when I go to reinstall windows, it says that it wants to format a partition on my ubuntu hard drive... this I obviously don't want, especially since I was asking it to specifically install it on the drive with windows already on it...

I don't know why it's doing this but I don't know how to get around this, any ideas? Should I make a new thread? 
:(

Ok... so you have Ubuntu on hda and Windows on hdb, two separate drives? if so just unplug hda and install windows on hdb, once you have windows installed re-connect hda and re-install grub. You can follow this thread to re-install grub: [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by Gleep on 2008-02-12
Thanks for your reply :)

In the end I sorted it out by just unplugging my Ubuntu drive and setting my windows drive to the master, currently putting all my backed up stuff back hah. Big job this...

---

### Post by Salpiche on 2008-02-12
> **Gleep said:**
> Thanks for your reply :)

In the end I sorted it out by just unplugging my Ubuntu drive and setting my windows drive to the master, currently putting all my backed up stuff back hah. Big job this...

Great, now all you need to do is mark this thread as Solved! :D

---

### Post by Gleep on 2008-02-12
> **Salpiche said:**
> Great, now all you need to do is mark this thread as Solved! :DI don't know how :$

---

### Post by Yellow Pasque on 2008-02-12
I believe there's an option under the Thread Tools menu (right above the first post)

---

### Post by Gleep on 2008-02-13
Thank you :)

---

