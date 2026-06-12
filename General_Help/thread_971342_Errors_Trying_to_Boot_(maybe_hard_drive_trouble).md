---
title: "Errors Trying to Boot (maybe hard drive trouble?)"
date: 2008-11-04
forum: General Help
---

### Post by chickendude on 2008-11-04
About a month ago i tried to shut down my computer and it threw an error and refused to turn on after that. I sent my computer in to have it fixed, but took out the harddrive hoping to keep my files and stuff. I got it back a few days ago and it will turn on now, but it won't boot all the way. After the Ubuntu logo with the loading bar, it gets about a third of the way through and drops to a screen where this error comes up dozens of times:
```
Exception Emask 0x0 SErr 0x0 action 0x0
(BMDMA stat 0x25)
cmd c8/00:08:4f:6f:47/00:00:00:00
```
and after a little while, i see this:
```
Error inserting: parport_pclib (/modules/2.6.22-15/generic/kernel/drivers/parport/parport_pc.ko) Bad Address
```
and then it repeats the other message for a while.
Eventually, it stops and gives me these messages:
```
Buffer I/O error on device sda1, logical block 4882434
Error reading block 4882434 (attempt to read block from filesystem resulted in short read) while getting next inode from scan
/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck manually
fsck died with exit status 4
...
*An automatic filesystem check (fsck) of the root filesystem failed
...
*The root filesystem is currently mounted in read-only mode
```And there it drops to the terminal prompt. After typing "fsck -y" and waiting a little while for it to finish running, if i restart the computer it will go through the whole process again but instead of dropping to the terminal it continues to boot and i can log in, however if i try to do anything in an application, it will frequently freeze for anywhere between a few seconds to a few minutes.

I was reading online that it may be that my hard drive is dying, but this is a pretty new laptop. I don't know how long a hard drive will usually last, but the older desktop computers (one which came with Windows 95, the other with 98) that i have are still in good shape. My laptop is about 2-3 years old :/

EDIT: Oh, and when i restart the computer after logging in, the trouble starts all over again (refusing to load all the way and dropping to the terminal).

---

### Post by steveydoteu on 2008-11-04
The first error is regarding a kernel module.

More to the point though if you have a spare harddrive that you can test with, I would suggest doing so.

---

### Post by chickendude on 2008-11-05
I don't have an extra hard drive lazing around, unfortunately. Once logged in, however, it says there are a few updates to install, but trying to install them leaves me with this message:
```
E:/var/cache/apt/archives/linux-image-2.6.22-15-generic_2.6.22-15.59_i386.deb: failed in buffer_read(fd)
```
and running "sudo dpkg --configure -a" gives me:
```
dpkg: error processing linux-image-2.6.22-15-generic (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 linux-image-2.6.22-15-generic
```(I am not able to reinstall it either). I don't know if this says anything helpful, but maybe it is the reason for the kernel errors?

---

### Post by chickendude on 2008-11-06
Hmm, another curious thing that has happened twice in a row now is a minute or two after opening Azureus, everything starts complaining that the hard drive is read-only and I can't save/download anything. Last time, rebooting and running "fsck" again set it back to normal (albeit, with a lot of freezes again, which seem to become less frequent after the computer has been turned on for about an hour. Initially, everything that I do freezes the computer for 20 seconds - maybe a minute and a half). Could this all be caused by me mishandling my hard drive or replacing it into the computer incorrectly? I stored it in an airtight bag in an out-of-the-way place in the closet... Hmm.. again, any help is appreciated! Thanks!

EDIT: I don't know if this is important or not, but I have been able to browse the Internet during this, so I think that means something is being downloaded somewhere...

---

### Post by TeXtonyx on 2008-11-06
Well, it seems like you could backup important files to a USB stick
then delete the Ubuntu partition(s) and reinstall it from the live cd.

---

### Post by chickendude on 2008-11-07
I guess that's what I'll have to do. For me, Ubuntu runs really well for a while, and then one day it just crashes on me. I've reinstalled Ubuntu many times (four or five separate occasions?) in the past twoish years since I've been using it, and I'm not quite sure what's happened any of those times. It just stops booting up :/ It just runs so well most of the time, and I can't really imagine heading back to Windows now. Oh well...

---

### Post by tvtech on 2008-11-07
it sounds like you have a hardware failure.  you should check around see if there are any disk analysis systems out there.   I've had Ubuntu running stable on three different machines with no issues other than ones I've caused by ...... editing certain files I should not have.    <--- I"m always one for trying something I don't know how to do. 

I would be willing to bet that either you've got a piece of hardware that is causing a conflict somewhere or something is failing.  I'd buy a new hardrive and go from there. they are cheep and usually *unless your unfortunate enough to own a mac easy to install.

---

### Post by y@w on 2008-11-07
I'd get your data off that hard drive and replace it.. Sounds like either a failing drive or a failing controller on the motherboard. I fought an issue with my MacBook for a couple of months where it would randomly hang then start working again. I started getting filesystem errors just a couple of days before it died.

---

### Post by chickendude on 2008-12-06
I'm not sure how to extract the data off of it, and anyways I think it's too late as a couple weeks ago I (unsuccessfully) tried to do a clean install of Ubuntu. I have an extended warranty from Toshiba so I think I'm just going to cave in and send it in the repair depot.

---

