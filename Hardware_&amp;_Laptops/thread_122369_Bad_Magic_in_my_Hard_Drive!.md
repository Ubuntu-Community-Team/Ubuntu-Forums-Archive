---
title: "Bad Magic in my Hard Drive!"
date: 2006-01-27
forum: Hardware &amp; Laptops
---

### Post by MrFahrenheit on 2006-01-27
I'm having a serious problem with one of my hard drives.

During boot the mounting fails and it asks me to log in as root or hit control-d.

I get the following messege:

```
e2fsck: Bad magic number in super-block while trying to open /dev/hdd1


The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
     e2fsck -b 8193 <device>
```

So, i run "sudo e2fsck -b 8193 /dev/hdd1" and it returns exactly the same error message!

I would really love to get my data off that drive.  It's a drive seperate from my main that only contains my pictures and music.

Can anyone help me fix this?

---

### Post by Nameless on 2006-01-27
I'm having the exact same problem.  When did you notice the problem beginning?  Did you resize a partition by any chance?

---

### Post by MrFahrenheit on 2006-01-27
no, i came home from work and my computer was sitting at the screen.  I assume there was a power outage.

---

### Post by az on 2006-01-27
Try to image the partition to save it

dd if=/dev/hdd1 of=file
if you have enough free disk space.

You can use a tool like foremost to retrieve photos and other file types from the image.

[http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)

You may be able to fix the partition itself, but I am not sure, myself.

---

### Post by Nameless on 2006-01-27
[QUOTE=azz]

dd if=/dev/hdd1 of=file
if you have enough free disk space.

[/QUOTE]

I'm going to try this, but for /dev/hda5.  Where would this save the image if I use the above command?

---

### Post by mips on 2006-01-28
Where you have space. I did this the other day but with a cd, I just executed the command from the same partition/folder where I wanted the image to be, that simple.

---

### Post by MrFahrenheit on 2006-01-28
what if that was my largest partition?  what can I do then?

---

### Post by az on 2006-01-28
You can run foremost on the partition directory, I think.  It won't write anything to the partition.  It is just prudent to image a partition before you try to salvage it.

You can tell foremost to only get jpegs or other file types.

---

### Post by MrFahrenheit on 2006-01-28
[QUOTE=azz]You can run foremost on the partition directory, I think.  It won't write anything to the partition.  It is just prudent to image a partition before you try to salvage it.

You can tell foremost to only get jpegs or other file types.[/QUOTE]


Ok, when you say "partition directory", do you mean the directory that the drive normally mounts to?

also, I've install foremost, but I'm getting confused about the options.  Can someone tell me how I would use it to get all .jpg, .ogg, and .mp3 files out of the drive please?

Thank you

---

### Post by MrFahrenheit on 2006-01-29
also, what could have caused this problem that I'm having?  Is the drive dying?

---

### Post by az on 2006-01-29
[QUOTE=MrFahrenheit]Ok, when you say "partition directory", do you mean the directory that the drive normally mounts to?

also, I've install foremost, but I'm getting confused about the options.  Can someone tell me how I would use it to get all .jpg, .ogg, and .mp3 files out of the drive please?

Thank you[/QUOTE]


Eeep!  I meant "partition directly"  Meaning you don't have to mount it.  Sorry!

---

### Post by MrFahrenheit on 2006-02-03
So far, all I've been able to do with foremost is get files that were on the hard drive when it used to be an NTFS windows drive.

How can I use foremost to grab the stuff that I had on it after I converted it to a linux drive?

Or, how can I just fix the hard drive?

---

