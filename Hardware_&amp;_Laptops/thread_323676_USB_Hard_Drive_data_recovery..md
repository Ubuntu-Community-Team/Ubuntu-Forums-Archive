---
title: "USB Hard Drive data recovery."
date: 2006-12-22
forum: Hardware &amp; Laptops
---

### Post by McLaughysSN on 2006-12-22
Hey guys, 

My company was running a USB harddrive on the network for contracts and other company information. Today  is started acting a little funny and eventually crashed. Now it's saying that the drive is not formatted when you try to access it. When you access the drive in linux, I see the permissions (I assumed it was unix based). 

I dont think i have my NTFS drivers loaded on this machine to access the windows portion of the drive. What should I try in order to access that information after I get the drivers loaded.

Thanks a million

---

### Post by McLaughysSN on 2006-12-22
joe@joe-laptop:~$ sudo mkdir /windoze
Password:
joe@joe-laptop:~$ sudo umount /dev/sda1
joe@joe-laptop:~$ sudo mount -t ntfs /dev/sdb1 /windoze -o nls=utf8,umask=0222
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

joe@joe-laptop:~$

I tried to mount the partition thinking that was the problem. and that is the message i received. when i check 'disks' in administration, it sees the windows partition (/dev/sdb1) on the drive, but it is labaled as inaccessable.

---

### Post by Cathead Fred on 2006-12-22
Hi McLaughysSN,

 Sorry to hear about your problem. I've heard really great things about a program called Spinrite. You can download a copy of it from [www.grc.com](www.grc.com). I think it costs around 80 bucks. It should help with recovering your data. It works with Linux and Windows. Read the reviews about what it can do.

 You may have to take the drive out of it's case and install it in a spare machine in order for Sprinrite to boot to it. Good luck.
 
Cathead Fred

---

### Post by UniRecovery on 2007-02-12
Whatever you do, do not format the USB- Good Luck

---

