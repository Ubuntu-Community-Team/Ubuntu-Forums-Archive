---
title: "Renaming/Reassigning existing CD/DVD writers to new devices/mount points"
date: 2007-01-25
forum: Hardware &amp; Laptops
---

### Post by disturbedite on 2007-01-25
i just copied and pasted this over from my post on the kubuntu forums since no one replied.  i also did a search first, but couldn't really find an answer to my question.  this is the closest thing i found, but i'm not quite sure if this applies to my question or not...  [http://ubuntuforums.org/showthread.php?t=233072](http://ubuntuforums.org/showthread.php?t=233072)

i'm gonna try to keep this simple, since others more in the know than i will prolly know the easy solution.

here is what i wanna do:
i have my cdwriter assigned as follows:  /dev/hda  /media/cdrom
i have my dvdwriter assigned as follows:  /dev/hdb  /media/dvdrom

i want to reassign both the devices and mount points respectively to this:
cdwriter:  /dev/cdwriter  /media/cdwriter
dvdwriter:  /dev/ddvdwriter /media/dvdwriter

how do i do that?  i need to use udev right?  what options and what not should i use?  i'd like to "rename" the original devices (hda/hdb) or create new ones if necessary.

---

### Post by K.Mandla on 2007-01-26
> **disturbedite said:**
> i just copied and pasted this over from my post on the kubuntu forums since no one replied.  i also did a search first, but couldn't really find an answer to my question.  this is the closest thing i found, but i'm not quite sure if this applies to my question or not...  [http://ubuntuforums.org/showthread.php?t=233072](http://ubuntuforums.org/showthread.php?t=233072)

i'm gonna try to keep this simple, since others more in the know than i will prolly know the easy solution.

here is what i wanna do:
i have my cdwriter assigned as follows:  /dev/hda  /media/cdrom
i have my dvdwriter assigned as follows:  /dev/hdb  /media/dvdrom

i want to reassign both the devices and mount points respectively to this:
cdwriter:  /dev/cdwriter  /media/cdwriter
dvdwriter:  /dev/ddvdwriter /media/dvdwriter

how do i do that?  i need to use udev right?  what options and what not should i use?  i'd like to "rename" the original devices (hda/hdb) or create new ones if necessary.
I've never heard of anyone doing this. I think the /dev/hdX names are carved in stone, because I think they are assigned in relation to where they exist as primary/secondary master/slave drives. 

But I think you could pick the mountpoints in your /etc/fstab file. Just make folders called /media/cdwriter and /media/dvdwriter, then mount the /dev/hda to /media/cdrwriter in fstab. Do the same for /dev/hdb.

Make sure your folder permissions are correct, or you'll end up with mounted but inaccessible drives. And I have **no** earthly idea how programs and software access to those drives is going to respond. I've never done this, so if your system ends up borked ... well, I'll just say, "Make sure you make a backup copy of your fstab file first." :biggrin:

---

### Post by disturbedite on 2007-01-26
> **K.Mandla said:**
> I've never heard of anyone doing this. I think the /dev/hdX names are carved in stone, because I think they are assigned in relation to where they exist as primary/secondary master/slave drives. 

But I think you could pick the mountpoints in your /etc/fstab file. Just make folders called /media/cdwriter and /media/dvdwriter, then mount the /dev/hda to /media/cdrwriter in fstab. Do the same for /dev/hdb.

Make sure your folder permissions are correct, or you'll end up with mounted but inaccessible drives. And I have **no** earthly idea how programs and software access to those drives is going to respond. I've never done this, so if your system ends up borked ... well, I'll just say, "Make sure you make a backup copy of your fstab file first." :biggrin:

thanks for the suggestion.  i know how to change mount points.  but i guess my question was directed more at changing the device name...

---

