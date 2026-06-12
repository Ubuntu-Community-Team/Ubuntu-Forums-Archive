---
title: "So far... can't mount my ZIP drive....."
date: 2006-11-12
forum: Hardware &amp; Laptops
---

### Post by Izobalax on 2006-11-12
Hey all. 

Firstly, I'm running Ubuntu Dapper Drake 6.06 on an Apple Mac PowerPC G3/400 Blue/White. 

Secondly, I have this ZIP drive. I've looked at other threads and tried to follow the advice, usually doing stuff in the terminal but without success. In the Device Manager, my ZIP drive is listed as /dev/hdb4.

How do I go about mounting it? I have a ZIP disk in there and it's ***stuck!*** :oops:

---

### Post by kidders on 2006-11-12
Hi there,

What have you tried so far?

To mount your zip disk, all that should be required is something like **mount /dev/hdb4 /mnt/wherever**.

What do you mean by "stuck" exactly? Does **eject /dev/hdb** do nothing for you? Is it jammed?

---

### Post by Izobalax on 2006-11-12
> **kidders said:**
> Hi there,

What have you tried so far?
Hi Kidders,

I tried a link someone posted in another thread similar to this query, and it was all things done in the Terminal (sorry, n00b speak!). I was able to make a directory for the mounting of the ZIP drive, but it couldn't actually find it. 

> **kidders said:**
> 
To mount your zip disk, all that should be required is something like **mount /dev/hdb4 /mnt/wherever**.
What would I type in as 'wherever'?

> **kidders said:**
> 
What do you mean by "stuck" exactly? Does **eject /dev/hdb** do nothing for you? Is it jammed?
I inserted a ZIP disk, but because I can't mount the ZIP drive, I can't eject it. If I try, I get this:[I]

"eject: unable to find or open device for: `/dev/hdb4'"[/I]

---

### Post by kidders on 2006-11-12
Hey again,

In threads like these, specific command sequences & error messages are tremendously helpful, but let's see how we do without them :-)

The first thing is this though: Since you're a Mac user (so am I :-) ), "eject" is probably an ambiguous term for you. In Linux, you don't "eject" a filesystem per se ... so your system's attempt to eject /dev/hdb4 will fail. In case you don't already know this, note that /dev/hdb refers to the actual storage device (zipdisk) itself, whereas /dev/hdb1, /dev/hdb2, etc. refer to individual partitions on it. So, if you'd like to get your disk back, try dropping to a terminal and typing **sudo eject /dev/hdb**.

(The eject will fail though, if another process is stuck in a loop, waiting on your disk to do something ... which can often happen when things aren't working for you.)

Now, once it's out, put it back in and start fresh. Check **dmesg** for any suggestion your disk might have auto-mounted. Assuming it doesn't, try this:
```

sudo mkdir /mnt/zipdisk
sudo mount /dev/hdb4 !$

```
If it works, neither command will produce any output, and your disk will be mounted at /mnt/zipdisk by root. This means "normal" users will have very limited access.

If you can get this far, everything is working perfectly.

[LIST=1]
[*]Unmount the disk again with **sudo umount /mnt/zipdisk** or **sudo umount /dev/hdb4**.
[*]Add an entry to your /etc/fstab (example below).
[*]Log out of your graphical environment and log back in again. Some environments are /etc/fstab-aware, in that they may now display an icon for your zip drive.
[/LIST]

So, here's an /etc/fstab suggestion for a removable FAT32 filesystem:

**/dev/hdb4 /mnt/zipdisk vfat rw,noexec,noauto,users,umask=026 0 0**

Of course, just because it would suit me, doesn't mean you'll like it, but the line should be a fairly safe starting point for you :-)

---

### Post by Izobalax on 2006-11-12
> **kidders said:**
> Hey again,

In threads like these, specific command sequences & error messages are tremendously helpful, but let's see how we do without them :-)

The first thing is this though: Since you're a Mac user (so am I :-) ), "eject" is probably an ambiguous term for you. In Linux, you don't "eject" a filesystem per se ... so your system's attempt to eject /dev/hdb4 will fail. In case you don't already know this, note that /dev/hdb refers to the actual storage device (zipdisk) itself, whereas /dev/hdb1, /dev/hdb2, etc. refer to individual partitions on it. So, if you'd like to get your disk back, try dropping to a terminal and typing **sudo eject /dev/hdb**.
Typing the command in your last line, I get this:

[I]"not an sg device, or old sg driver
eject: unable to eject, last error: Invalid argument"[/I]

> **kidders said:**
> 
(The eject will fail though, if another process is stuck in a loop, waiting on your disk to do something ... which can often happen when things aren't working for you.)
It certainly failed for me. 

> **kidders said:**
> 
Now, once it's out, put it back in and start fresh. Check **dmesg** for any suggestion your disk might have auto-mounted.
This gave me a list of command that I don't understand.

> **kidders said:**
> 
 Assuming it doesn't, try this:
```

sudo mkdir /mnt/zipdisk
sudo mount /dev/hdb4 !$

```
This gave me this response:

```
sudo mount /dev/hdb4 /mnt/zipdisk
mount: you must specify the filesystem type
```

> **kidders said:**
> 
If it works, neither command will produce any output, and your disk will be mounted at /mnt/zipdisk by root. This means "normal" users will have very limited access.

If you can get this far, everything is working perfectly.
Not for me. 

> **kidders said:**
> 
[LIST=1]
[*]Unmount the disk again with **sudo umount /mnt/zipdisk** or **sudo umount /dev/hdb4**.
Both commands give me this:

```
umount: /dev/hdb4: not found
```

> **kidders said:**
> 
[*]Add an entry to your /etc/fstab (example below).
[*]Log out of your graphical environment and log back in again. Some environments are /etc/fstab-aware, in that they may now display an icon for your zip drive.
[/LIST]

So, here's an /etc/fstab suggestion for a removable FAT32 filesystem:

**/dev/hdb4 /mnt/zipdisk vfat rw,noexec,noauto,users,umask=026 0 0**

Of course, just because it would suit me, doesn't mean you'll like it, but the line should be a fairly safe starting point for you :-)
Nope, sorry, Ubuntu still can't mount the ZIP disk. :-k

---

### Post by kidders on 2006-11-12
Hmm... it looks as though your zip drive might not be at /dev/hdb after all ... and even if it is, it may not be formatted. How did you determine that that's where it's at?

For instance, on my machine, **dmesg | grep -i zip** gives me:
```
hdc: IOMEGA ZIP 100 ATAPI, ATAPI FLOPPY drive
``` indicating that, at some point during startup, Ubuntu detected my device. It also tells me where it is (/dev/hdc). How about you?

**Edit:**
By investigating a little further, with, say **dmesg | grep -i hdc**, i find ...
```
[17179588.360000] hdc: No disk in drive
[17179588.408000] hdc: 98304kB, 32/64/96 CHS, 4096 kBps, 512 sector size, 2941 rpm
[17179588.896000] hdc: No disk in drive
[17179589.808000] hdc: No disk in drive
[17179591.456000] hdc: No disk in drive
[17537939.164000] hdc: 98304kB, 196608 blocks, 512 sector size
[17537939.260000]  hdc: hdc4

```
... showing me some of the things that have been going on with the device, since my last boot.

---

### Post by Izobalax on 2006-11-12
> **kidders said:**
> Hmm... it looks as though your zip drive might not be at /dev/hdb after all ... and even if it is, it may not be formatted. How did you determine that that's where it's at?

For instance, on my machine, **dmesg | grep -i zip** gives me:
```
hdc: IOMEGA ZIP 100 ATAPI, ATAPI FLOPPY drive
``` indicating that, at some point during startup, Ubuntu detected my device. It also tells me where it is (/dev/hdc). How about you?
This command gives me this message:

```
[   37.944474] hdb: IOMEGA ZIP 100 ATAPI, ATAPI FLOPPY drive
```

---

### Post by kidders on 2006-11-12
Heck! So you *do* have the right location ](*,)

In that case, we have to deal with "mount: you must specify the filesystem type". Linux is capable of recognising most filesystems in modern use, so chances are that your zip disk is unformatted. Could that be true?

I'd be interested in seeing the output of **fdisk -l /dev/hdb** -- If indeed the disk *is* unformatted, any attempt to mount a filesystem that doesn't exist will, of course, fail.

If the zipdisk _is_ alive and formatted, I'm afraid I might be out of suggestions :-( I'll think about it for a little while though ... see what I can come up with!

---

### Post by Izobalax on 2006-11-12
> **kidders said:**
> Heck! So you *do* have the right location ](*,)

In that case, we have to deal with "mount: you must specify the filesystem type". Linux is capable of recognising most filesystems in modern use, so chances are that your zip disk is unformatted. Could that be true?

I'd be interested in seeing the output of **fdisk -l /dev/hdb** -- If indeed the disk *is* unformatted, any attempt to mount a filesystem that doesn't exist will, of course, fail.
Well, I inserted the command, it accessed the ZIP drive, and the Terminal just gave me a new line to type from.

> **kidders said:**
> 
If the zipdisk _is_ alive and formatted, I'm afraid I might be out of suggestions :-( I'll think about it for a little while though ... see what I can come up with!
No worries. You've been a great help. ;)

---

### Post by kidders on 2006-11-12
Oh really? That's what mine does when there's no disk in the drive at all. Are you sure the disk (or drive) isn't damaged in some way that's preventing the drive from realising a disk has been inserted?

I may be wrong, but afaik, if the drive is working properly, there should be at least *some* output ... even if the disk is blank or broken.

---

### Post by Izobalax on 2006-11-12
> **kidders said:**
> Oh really? That's what mine does when there's no disk in the drive at all. Are you sure the disk (or drive) isn't damaged in some way that's preventing the drive from realising a disk has been inserted?

I may be wrong, but afaik, if the drive is working properly, there should be at least *some* output ... even if the disk is blank or broken.
I have no idea on how to establish this. I would take my disc out, of course, but I can't.

---

### Post by kidders on 2006-11-12
This must be very frustrating for you!

In any case, if you were to power off your computer, the disk should eject during the boot process when you hit the button. If it doesn't, I'm afraid you have a hardware failure.

**Edit:**
Does your drive have a manual release trigger? (Mine doesn't!) If so, an uncoiled paperclip will do the trick nicely for you.

---

### Post by Izobalax on 2006-11-12
> **kidders said:**
> This must be very frustrating for you!
Oh yes. ](*,) 

> **kidders said:**
> 
In any case, if you were to power off your computer, the disk should eject during the boot process when you hit the button. If it doesn't, I'm afraid you have a hardware failure.
Nah, I've rebooted the computer several times, and the ZIP disk is quite happy where it is. :-? 

> **kidders said:**
> 
**Edit:**
Does your drive have a manual release trigger? (Mine doesn't!) If so, an uncoiled paperclip will do the trick nicely for you.
I have no manual release..... but I'm not sure about getting paperclips involved in extracting disks.... especially when ***LIVE*** electrical equipment is so closely invovled.......... :-k

---

### Post by kidders on 2006-11-12
Does this drive/disk currently work with any other operating systems? I'm really starting to suspect a hardware failure :-(

---

### Post by Izobalax on 2006-11-12
Worked fine in Mac OS X Tiger.

---

### Post by tbrunk1 on 2006-11-13
Hello!

I have been following this discussion because I have the same problem. My zip drive is an internal IDE drive. It worked fine under XP, and has never worked with Ubuntu. My drive is hdb. My problems dito what is going on here, so I don't think it could be a hardware problem since my drive did work under XP.

---

### Post by kidders on 2006-11-14
Hmmm :-( If either of you manage to find the problem, I'd really like to know what it is! I'm afraid Izobalax and I weren't able to pin down the issue. ](*,) It's strange though, because I've never had any trouble with my IDE zip drive.

Please let me know if there's anything about my configuration you'd like to see, for comparison ... I can't really imagine what though.

---

