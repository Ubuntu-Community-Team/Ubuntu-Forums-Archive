---
title: "The enclosing drive for the volume is locked"
date: 2009-05-13
forum: Hardware
---

### Post by ((( ~ ))) on 2009-05-13
Hi everyone, this is my first thread so please treat me gently :p

So the problem is when I want to stick my 4GB USB drive (to make a persistent install), I get this weird error:

```
Unable to mount "NANO":

The enclosing drive for the volume is locked
```

What I've already tried:
1. I looked around on the forum and noticed this:
[http://ubuntuforums.org/showthread.php?t=1098884](http://ubuntuforums.org/showthread.php?t=1098884)

...but since I can't even open the properties, I think it's pretty useless to follow that thread right?

2. Opened gparted and saw the volume as formatted to NTFS (but there as well, drive not mounted). 

3. Tried different USB ports, but got the same results.


Really, any help would greatly be appreciated  :)

---

### Post by ((( ~ ))) on 2009-05-14
Update:

I formatted the pendrive with FAT32 2 times, and on the 2nd time it started to work :S
Anyway, I'm off to create a persistent USB install.

Just some minor questions:
1. Would the persistent install be loaded in RAM (like a liveCD?)?
2. How can I transfer my files, settings and apps to my main install on my new laptop?
3. I'm planning to have multiboot on my new laptop with (X)Ubuntu as my main, which should I install first, Xubuntu or winXP?

Thanks in advance :)

---

### Post by steve01832 on 2009-05-14
If this drive was used on another computer and it wasn't properly unmounted then Linux will report errors. If this is the case, put the drive in that machine and before you unplug it, make sure you unmount it first. If it's a Wi****s machine, click on the safely remove hardware button and select the drive. Wait until you are prompted to remove it before you disconnect it. 

Steve

---

### Post by ((( ~ ))) on 2009-05-16
> **steve01832 said:**
> If this drive was used on another computer and it wasn't properly unmounted then Linux will report errors. If this is the case, put the drive in that machine and before you unplug it, make sure you unmount it first. If it's a Wi****s machine, click on the safely remove hardware button and select the drive. Wait until you are prompted to remove it before you disconnect it. 

Steve

Thanks Steven, my USB stick has always been 'safely removed' in an M$ machine, but still gave me numerous errors when trying to (un)mount on Xubuntu, even when nothing (in sight) was accessing the stick.

Quite peculiar indeed, but, I think all the problems can be solved. They always can be... right? :-\"

Anyway, here's a thread explaining my misery in detail:
[http://ubuntuforums.org/showthread.php?p=7291335](http://ubuntuforums.org/showthread.php?p=7291335)

cya!

---

### Post by lauri___ on 2009-06-02
I was unable to read ntfs partition of Vista intsallation from gparted (partition editor)
It have been solved by installing ntfsprogs package using synaptics package manager.

---

### Post by Jatepola on 2009-11-12
> **lauri___ said:**
> I was unable to read ntfs partition of Vista intsallation from gparted (partition editor)
It have been solved by installing ntfsprogs package using synaptics package manager.

Thank you very much, mate. I had exactly the same problem (I use XFCE 4.4 and I sometimes could access that drive, but not this time) and your solution worked!

---

### Post by jbermellon on 2011-04-10
Well, I have the same problem, the thing is I also have a non working-not mounting Ext4 partition. The two are part of the same extended partition and, after installing an ntfs mounting manager, only the NTFS is getting mounted (though not listed in places as I think it should be -don't know, I'm new to Xubuntu, but have been using Maverick Meerkat for a while in my netbook-).

The error message is the same as the above. I've also used a live usb of Maverick and it has no problem mounting -and listing in places- the two drives. I'm about to stop using Xubuntu, but the thing is I really like the aesthetics and speed of it all.

Someone please help.

---

### Post by charisz on 2011-04-19
I have the same problem, with an ext4 partition. I'm waiting any tips too.

---

### Post by iateadonut on 2011-05-23
try e2fsck

---

### Post by flemur13013 on 2011-12-03
I was getting that error on a newly created ext4 partition on a USB drive. e2fsck said everything was OK. NTFS parts. on the same drive gave the same error.
I unmounted the only mounted part. on the drive then everything else mounted fine and worked ...!?

---

