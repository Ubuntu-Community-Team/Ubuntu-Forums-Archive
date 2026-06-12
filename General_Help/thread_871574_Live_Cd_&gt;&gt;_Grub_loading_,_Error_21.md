---
title: "Live Cd &gt;&gt; Grub loading , Error 21"
date: 2008-07-27
forum: General Help
---

### Post by terryfox on 2008-07-27
Hi , I try using the Live cd on my brother computer after I used it on my computer . well now my brother computer wouldn't load Vista . The bios start to load but stop with this error : Grub loading , Error 21 . Now what cause this to happen and why ? How can I fix this error ? I hope his computer isn't all lost . He already freak out on me and I really need for him to get his computer up and running Vista again . Please I need your help .

TIA

---

### Post by jimv on 2008-07-27
Hmmm.  Boot back up from the live CD and go to Applications > Accessories > Terminal to open a terminal.  Type 

sudo fdisk -l

Post the output back here.  You should be able to use Firefox from the Live CD.

---

### Post by terryfox on 2008-07-27
Hi, What step do you take to view everything on the system ? I want to view all the data within the PC . Thanks

---

### Post by Sef on 2008-07-27
This is GRUB error 21:

> 21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. 

---

### Post by terryfox on 2008-07-27
> **Sef said:**
> This is GRUB error 21:

Well I got this error when the damn Live cd froze and I had to use the power buttom to shut it down , Afterwards it screw the Vista drive and another separate drive from loading .

---

### Post by confused57 on 2008-07-27
For now, you could try reinstalling Vista's IPL to the mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
Super Grub Disk or a Vista install disk(not a recovery disk) would probably be the easiest methods.

I would recommend using the alternate install cd, if you try reinstalling Ubuntu.  Are you trying to install on a separate drive from Vista?

---

### Post by terryfox on 2008-07-27
> **confused57 said:**
> For now, you could try reinstalling Vista's IPL to the mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
Super Grub Disk or a Vista install disk(not a recovery disk) would probably be the easiest methods.

I would recommend using the alternate install cd, if you try reinstalling Ubuntu.  Are you trying to install on a separate drive from Vista?


Well that was the PROBLEM I didn't realize it would cause such a nightmare to install and yes I did try to unto a different drive . Now this drive and my Vista drive are F_____d . I think Ubuntu team should mention this , that it could happen . I mean at least give some sore of a warnning , If I would of knew I wouldn't of bother . Now I'm screw , Thanks for the link

---

### Post by confused57 on 2008-07-27
> **terryfox said:**
> Well that was the PROBLEM I didn't realize it would cause such a nightmare to install and yes I did try to unto a different drive . Now this drive and my Vista drive are F_____d . I think Ubuntu team should mention this , that it could happen . I mean at least give some sore of a warnning , If I would of knew I wouldn't of bother . Now I'm screw , Thanks for the link
The Vista install shouldn't be affected in any way, restoring the mbr should restore the ability to boot Vista.

The alternate install cd is recommended for computers with less than approximately 380 Mb ram.

Added:  If the hard drives are IDE, you might try going into the bios setup and make sure the Ubuntu drive's IDE controller is set to "Auto" or "Enabled".  Error 21 would result if the IDE controller is set to "Off".

---

### Post by terryfox on 2008-07-27
> **confused57 said:**
> The Vista install shouldn't be affected in any way, restoring the mbr should restore the ability to boot Vista.

I like to know why it did that ? I even formated the Vista drive and try using True Image to restore a backup image,  I still end up getting that error afterwards , very disappointed I must say .

> **confused57 said:**
> 
The alternate install cd is recommended for computers with less than approximately 380 Mb ram.

Added:  If the hard drives are IDE, you might try going into the bios setup and make sure the Ubuntu drive's IDE controller is set to "Auto" or "Enabled".  Error 21 would result if the IDE controller is set to "Off".

I am running Vista , which computer can run Vista with 380 mb ram or less ? I was dual booting with Vista and XP both on separate drives , Even the drive that Ubuntu try to install was a different drive .

---

### Post by terryfox on 2008-07-27
Forgot to mention all my controllers are on Auto . This OS was written badly I believe .

---

### Post by terryfox on 2008-07-28
Ok , so I gave it another try on just a XP pc and it work perfectly . So now i'm thinking it just not Vista supported . If it is ? Not very well .

---

### Post by Sef on 2008-07-28
When partitioning for Ubuntu, did you use the Live CD partitioner (GParted) or the Vista partitioner?

---

### Post by terryfox on 2008-07-28
> **Sef said:**
> When partitioning for Ubuntu, did you use the Live CD partitioner (GParted) or the Vista partitioner?

It was from the Live cd .

---

