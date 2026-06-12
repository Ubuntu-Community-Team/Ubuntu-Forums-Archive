---
title: "USB Flash Drives not Mounting"
date: 2012-10-15
forum: Hardware
---

### Post by OutlandishKnight on 2012-10-15
Ubuntu is failing/refusing to mount any USB flash drives. I've tried a number of possible solutions from previous, similar threads to no avail. Since this has been going on a few weeks due to busy-ness, I've slightly lost track of what I have tried, but I can say that mounting it manually doesn't work and, though usb_storage was missing from /etc/modules, adding it has made no difference so far.

Also worth mentioning: When I'm monitoring the system log in a terminal, it detects a drive being inserted and removed so Ubuntu isn't completely failing to see it. It shows up with the lsusb command and fdisk -l. With fdisk -l , though, everything else shows up immediately but the drive takes several minutes to appear.

Oh, and of course I've checked that automount is actually turned on.

Any help gratefully appreciated.

---

### Post by dniMretsaM on 2012-10-15
Is it possible to mount it via the command line?

```
sudo mount /dev/xxxy /path/to/mount/point/
```

[FONT=Courier New]xxx[/FONT] represents your USB drive (possible sdb. fdisk -l will tell you) and [FONT=Courier New]y[/FONT] is the partition number you want to mount (probably 1).

---

### Post by OutlandishKnight on 2012-10-16
That's the method I used when attempting to mount manually (last tried just before starting this thread), and unfortunately it doesn't work.

Previously I was getting an error message. But I just did it once more to remind myself what that message was, and this time it's just doing nothing. Apparently the process is running, so I'm leaving it to it. It's been a while and nothing yet, so I'm giving in and making a post for now, but I'll update if anything actually happens.

UPDATE: Always the way, it finally did something two minutes after I finally decided to post. I'm pretty sure this is a different error message from before, but here's what I got this time:

```
mount: /dev/sdb already mounted or /media/external busy
```

EDIT 2: Just realised typed it as just sdb this time instead of sdb1 as before (and as your instruction suggests), but so far with sdb1 taking ages again so guessing will be same result.

---

### Post by Parker32 on 2012-10-17
Sounds like a defective flash drive to me, since it has problems mounting on a Windows system as well. Reformatting it may help with the problem, though; worth a try, anyway.

BTW, this forum is for older, pre-1999 systems, and so not the best place to post about issues with more recent systems.

---

### Post by OutlandishKnight on 2012-10-17
Actually, the the flash drive seems to work fine on Windows systems, and I've tried other ones with Ubuntu and got the same results, so I don't think it's the flash drive that's at fault.
 
Apologies about the forum mix-up. I thought I'd got the hardware section of the general Ubuntu support forum.

---

### Post by OutlandishKnight on 2012-10-17
Tried formatting it anyway, to no avail. Also, contrary to my previous statement, when I try formatting by terminal and specify SDB1 it says that doesn't exist. But fdisk -l says otherwise.

---

### Post by OutlandishKnight on 2012-10-18
Given the lack of success with various solutions I'm starting to seriously wonder if I've hit a brick wall. I hope nobody minds me bumping this thread once more before I resort to reinstalling Ubuntu. I know that's probably a bit drastic, hence my wanting to be sure nobody has better ideas first, but if that's what it takes I'd rather get my flash drives working again.

---

### Post by Bashing-om on 2012-10-18
OutlandishKnight; Hi !

How about this approach, make a mount point, and see if you can mount the device manually ?
```
sudo mkdir /mnt/usb
sudo mount /dev/sdb1 /mnt/usb
```this assumes your usb device is recognized as sdb1 - change as appropriate.

edit: not known how this will interact with windows format, may take adding options ?
[INDENT]hth <==BDQ
 

[/INDENT]

---

### Post by OutlandishKnight on 2012-10-19
Thanks Bashing-om, that's something I've previously tried (sorry I've been so vague about what I've done before, but as I say between number of things and length of time I've lost track a bit). However, could you please clarify what you mean about adding options because of the windows format? 
 
Also, since Ubuntu seems to be at least seeing it, is there a way I could format again with Ubuntu through the terminal if there's any chance it would help?

---

### Post by James D. Moore on 2012-12-25
:confused:
Anyone have a copy and paste solution as I am dislectic and have AADDS
aoutomount worked before update so wtf?

---

### Post by James D. Moore on 2012-12-25
If you get a Good solution give me a git back here or my email [email]winstonchalmer@yahoo.com[/email] 
thanks much Dave

---

