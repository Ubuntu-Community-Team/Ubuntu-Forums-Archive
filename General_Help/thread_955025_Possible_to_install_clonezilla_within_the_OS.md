---
title: "Possible to install clonezilla within the OS?"
date: 2008-10-21
forum: General Help
---

### Post by josephellengar on 2008-10-21
,.. so I don't have to use a livecd to run it?

---

### Post by bodhi.zazen on 2008-10-21
Normally you need to manage your partitions from a live CD as they need to be unmounted when you manipulate them (image, resize, etc).

You can install gparted or other applications and use them to manage all but your root partition.

---

### Post by cazz on 2009-03-24
Hi
have the same question.
I was thinking about have a small Linux on the laptop with a nice bootmenu so if I want I can start Linux and do a recovery for my windows XP from a image to a partion. 

but I have not find any nice program that can do that for me yet.

---

### Post by bodhi.zazen on 2009-03-24
> **cazz said:**
> Hi
have the same question.
I was thinking about have a small Linux on the laptop with a nice bootmenu so if I want I can start Linux and do a recovery for my windows XP from a image to a partion. 

but I have not find any nice program that can do that for me yet.

Depends on what you want exactly. gparted or prartimage are two of several options (as are tar and dd ).

---

### Post by duffydack on 2009-03-24
it tells you on the clonezilla site about booting it from a partition on hd, and also makin usb stick which is what i use

---

### Post by cazz on 2009-03-24
> **bodhi.zazen said:**
> Depends on what you want exactly. gparted or prartimage are two of several options (as are tar and dd ).

well I can use other then clonezilla to create a restore system for a laptop. I just need what to look after and some good site with information :)

---

### Post by cazz on 2009-03-24
> **duffydack said:**
> it tells you on the clonezilla site about booting it from a partition on hd, and also makin usb stick which is what i use

Only did find information about something else but if I can use another program then clonezilla I can use that instead

---

### Post by fishman35 on 2011-07-22
I use Clonezilla in place of Symnatec Ghost and have to image multiple systems at the same time. It used to work well in Ubuntu 7, but seems like in 10.4, 10.10, and 11, there have been multiple problems with just getting it installed correctly. Unstable DBRL servers to download the files, invalid keys, etc.

---

### Post by Redsandro on 2011-07-22
Yes that would be desirable. Like booting from a Live USB and installing gparted [SIZE="1"](although nowdays it's included by default)[/SIZE] was a way to go, it would be nice to be able to install Clonezilla in the same way.

---

### Post by Mark Phelps on 2011-07-23
> **Redsandro said:**
> Yes that would be desirable. Like booting from a Live USB and installing gparted [SIZE="1"](although nowdays it's included by default)[/SIZE] was a way to go, it would be nice to be able to install Clonezilla in the same way.

Then ... go to the Clonezilla website.  

They have a FAQ that provides the details of adding CloneZilla to your /boot folder in a way that when you boot, you see a GRUB menu with an entry for CloneZilla -- and can boot to that.

---

