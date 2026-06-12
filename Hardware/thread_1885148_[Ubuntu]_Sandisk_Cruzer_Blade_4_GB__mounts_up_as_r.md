---
title: "[Ubuntu] Sandisk Cruzer Blade 4 GB  mounts up as readonly for Ubuntu. (Fine on Win7)"
date: 2011-11-22
forum: Hardware
---

### Post by SirTheSurfer on 2011-11-22
I wanted to make bootable installation of Windows 7 on my pendrive so I formated it with help of gparted to NTFS. After that I can't do notching but copy or view files from it (Most probably problem existed earlier but I hadn't any chance to know about it) Moreover device works fine on Eeepc Netbook of my friend where Windows 7 is installed.- My vehicle is Eee PC 1215N.

I've asked my friend from group who knows Linux better than me but it  occurred his abilities aren't enough. I've been looking for similar  problems in Internet but couldn't find any...And thats the story of how I ended up writing here.

---

### Post by Mark Phelps on 2011-11-22
When the USB stick was being used in the Win7 PC, did you just pull it out? Or, did you click in the task area, the USB icon with the green arrow, and "safely remove" it?

If you did the former, you left the NTFS file system in an interim state -- and in those cases, Ubuntu default to mounting it read-only to prevent further damage.

Put the stick back into the Win7 machine. If it mounts it OK, then Safely Remove it.  IF it doesn't, you may need to run CHKDSK on it, and THEN, Safely Remove it.

---

### Post by SirTheSurfer on 2011-11-22
> **Mark Phelps said:**
> When the USB stick was being used in the Win7 PC, did you just pull it out? Or, did you click in the task area, the USB icon with the green arrow, and "safely remove" it?

If you did the former, you left the NTFS file system in an interim state -- and in those cases, Ubuntu default to mounting it read-only to prevent further damage.

Put the stick back into the Win7 machine. If it mounts it OK, then Safely Remove it.  IF it doesn't, you may need to run CHKDSK on it, and THEN, Safely Remove it.

Currently I don't have any means to stick my naughty pen in any computer with win7 on board. Besides problem didn't occur after stucking it to vehicle with Windows 7 - I did it for diagnostic purposes after when I found out that it doesn't work properly with my Eee PC,with Ubuntu on board. I used netbook of my friend - also Eee PC.

---

### Post by Mark Phelps on 2011-11-23
If the USB stick mounts in Windows but not in Ubuntu, that is most likely the Unclean Removal problem. 

There is really no way to fix that in Ubuntu, as it will not mount as long as that problem remains.

Have you tried the suggestion for mounting it in a Windows PC and then Safely Removing it?

---

### Post by SirTheSurfer on 2011-11-23
> **Mark Phelps said:**
> If the USB stick mounts in Windows but not in Ubuntu, that is most likely the Unclean Removal problem. 

There is really no way to fix that in Ubuntu, as it will not mount as long as that problem remains.

Have you tried the suggestion for mounting it in a Windows PC and then Safely Removing it?

I've tried it on computer with XP on board just a minute ago and it didn't worked.

---

### Post by Mark Phelps on 2011-11-23
> **SirTheSurfer said:**
> I've tried it on computer with XP on board just a minute ago and it didn't worked.

That's not good news ... but "didn't worked" doesn't tell me anything other than it failed. And, it might have failed because it needs to have CHKDSK run on it.

Since you can't run CHKDSK from Ubuntu, you should plug it into the XP box again, click on Start and then Run. Type the following command in the text box and then hit the Enter key: diskmgmt.msc

Look through the list of "volumes" and see if the USB stick is listed.  It might be, but not have a drive letter.  Try assigning it a letter to see if that works.  IF so, you will then need to run CHKDSK on the volume.

---

### Post by OrangeCrate on 2011-11-23
> **SirTheSurfer said:**
> I wanted to make bootable installation of Windows 7 on my pendrive so I **formated it with help of gparted to NTFS**. After that I can't do notching but copy or view files from it (Most probably problem existed earlier but I hadn't any chance to know about it) Moreover device works fine on Eeepc Netbook of my friend where Windows 7 is installed.- My vehicle is Eee PC 1215N.

I've asked my friend from group who knows Linux better than me but it  occurred his abilities aren't enough. I've been looking for similar  problems in Internet but couldn't find any...And thats the story of how I ended up writing here.

I'm not sure, if my advice is what will specifically fix your problem, but, I reformat all of my sticks to FAT32 when I get them. I've never had a problem with any of them - they all work fine on both Windows and Linux.

---

### Post by SirTheSurfer on 2011-11-23
> **OrangeCrate said:**
> I'm not sure, if my advice is what will specifically fix your problem, but, I reformat all of my sticks to FAT32 when I get them. I've never had a problem with any of them - they all work fine on both Windows and Linux.

I've done like you have said and it have worked.-I was able to write/read my pen from Ubuntu. So first thing I've did I've burned iso image of Windows 7 on it (with "unetbootin" tool) 

Sadly, another problem occureed - it can't be ridden by my Eeepc- it says something like "media isn't bootable". I've checked if it indeed isn't bootable with help of "gparted" and the label of that device says "bootable"

---

### Post by OrangeCrate on 2011-11-24
> **SirTheSurfer said:**
> I've done like you have said and it have worked.-I was able to write/read my pen from Ubuntu. So first thing I've did I've burned iso image of Windows 7 on it (with "unetbootin" tool) 

**Sadly, another problem occureed - it can't be ridden by my Eeepc- it says something like "media isn't bootable". I've checked if it indeed isn't bootable with help of "gparted" and the label of that device says "bootable"**

If I understand your problem correctly, this is an issue I can't help you with. I'm sure someone else will be along that can...

I use sticks just for file storage and transfer between Windows and Linux boxes. I've never tried to install from a stick, I've always burned disks to do that.

Good luck.

---

### Post by SirTheSurfer on 2011-11-25
> **OrangeCrate said:**
> If I understand your problem correctly, this is an issue I can't help you with. I'm sure someone else will be along that can...

I use sticks just for file storage and transfer between Windows and Linux boxes. I've never tried to install from a stick, I've always burned disks to do that.

Good luck.

 
I've bought another pendrive and problem with writeability didn't occured- perhaps because I didn't format it to NTFS? Anyway, I downloaded "Universal USB" to my windows XP machine and there I burned Windows 7. It worked...As  soon as I'll install Debian or Ubuntu on my Netbook I'll speak up ( it won't be soon because I've got a lot to do now while I study thus I won't spend much time on learning Linux)

---

### Post by OrangeCrate on 2011-11-25
> **SirTheSurfer said:**
> I've bought another pendrive and problem with writeability didn't occured- perhaps because I didn't format it to NTFS? Anyway, I downloaded "Universal USB" to my windows XP machine and there I burned Windows 7. It worked...**As  soon as I'll install Debian or Ubuntu on my Netbook I'll speak up** ( it won't be soon because I've got a lot to do now while I study thus I won't spend much time on learning Linux)

I look forward to hearing how it all works out...

---

