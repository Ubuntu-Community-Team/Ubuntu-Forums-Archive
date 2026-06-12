---
title: "plugin USB hard disk. What controls permissions?"
date: 2008-12-04
forum: Hardware
---

### Post by l5nrr on 2008-12-04
**_short question_**
how can I control what happens when I plug in a USB hard disk and it automounts
[B][U]
long question[/U][/B]
Hardy Heron 8.04
note "automount" seems to be used in 2 ways. 1) detected & mounted at startup, ie via fstab. 2)detected & mounted when plugged in, eg a portable usb hard disk. My question is about 2).

I have a usb hard disk, formatted NTFS. When I plug it in, it is detected and mounted, as it should. But it's ownership and permisions are erratic. Two weeks ago I could write to it. Now I have no permission to write to it, nor to chown or chmod. It's current mtab entry is:-
```
/dev/sdc1 /media/LaCie fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0

```

Now I have easily got around this problem by putting an entry into fstab:-
```
UUID=888657D88657C4FA /media/usb_LaCie ntfs defaults,umask=007,uid=1000
```
When I plug the USB hard drive in, I get a message that says I don't have permissions to mount it, but no matter, 
	```
garry@toybox-hardy:~$ sudo mount -a
```
does the trick.

But I want it to mount predictably and usefully, automatically, when I just plug it in. So I suppose the question, what is it that decides and creates the old mtab entry. How can I control that?

thank you

---

### Post by Mewshi on 2008-12-04
I actually have this exact same problem, and this is why all the disks I use are either XFS (such as my "backup" SD card that sits in my laptop) or FAT32 (such as my USB Hard Drive)  It's very annoying.

---

