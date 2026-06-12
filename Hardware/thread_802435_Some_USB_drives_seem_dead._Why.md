---
title: "Some USB drives seem dead. Why?"
date: 2008-05-21
forum: Hardware
---

### Post by egruber on 2008-05-21
I am running Hardy on an IBM T40. I have a number of USB drives. Some of them work perfectly. Others don't work at all. I plug them in, but the little light on the drive stays out and the laptop behaves as if nothing was plugged in. All of them work perfectly on my XP machine. 

Other than the brand names and file capacities, the drives are pretty much the same. Any idea as to why some of them don't work? BTW, my wife had a similar problem on her MAC. She bought 5 drives..all the same. Some worked, some appeared dead. But all worked on my XP machine.

---

### Post by pytheas22 on 2008-05-21
Did you try mounting them on the command line?  That would give you a better idea of why the system is not aut0-mounting them.  If you don't know how to mount and can't figure it out by searching, ask here.

---

### Post by egruber on 2008-05-21
I'm really a newbie when it comes to command line entries.  If you could post some simple instructions, I will try to post the results.  Thanks!

---

### Post by pytheas22 on 2008-05-21
No problem.  To mount, you first need to know the device name assigned to the USB drive inside the /dev directory.  Typically this is sdX, where X is a letter like a, b, c...  If you only have one hard drive, the USB stick should be named sdb, or sdc if you have to hard drives, and so on.  Here I'll assume that you have one hard disk and that the USB drive is named sdb.

To mount it, you need to first create a mount point for it (Ubuntu usually deals with this automatically when you plug something in, but it may not be doing that for your stick).  This can be anywhere on the system, but in Ubuntu the convention is to use the /media directory.  So you would run:

```
sudo mkdir /media/sdb
```

Then you mount the device with:

```
sudo mount /dev/sdb /media/sdb
```

if something goes wrong, you should be told now.

Try this and see if the mount command tells you anything useful.

---

### Post by egruber on 2008-05-21
Tried it and here is what I got.  Any ideas?

eli@eli-laptop:~$ sudo mkdir /media/sdb
[sudo] password for eli: 

eli@eli-laptop:~$ sudo mount /dev/sdb /media/sdb
mount: special device /dev/sdb does not exist
eli@eli-laptop:~$

---

### Post by jbulcher on 2008-05-22
All drives aren't automatically assigned sdb, just as pytheas22 said; they are sdX where X is a letter assigned to the device. In order to determine what name the device has, just ```
cat /var/log/messages
``` right after you plug the device in. The name of the device will be near the end if its usable; just look for something that starts with 'sd'. Then use after /dev/ the way pytheas22 said.

*note* sometimes you need to mount a partition, rather than the whole drive, as is the case with hard drives. The partitions are designated by a number appended to the name of the device in the format sdX# *note*

Good luck!

---

### Post by ubonetu on 2008-05-22
Just chiming in...  I have the dmseg and /var/log/messages for my issue seems the same.

Even my printer is offline now.

Ward

---

