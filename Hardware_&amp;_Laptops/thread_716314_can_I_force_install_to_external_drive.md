---
title: "can I force install to external drive?"
date: 2008-03-05
forum: Hardware &amp; Laptops
---

### Post by Ozzz on 2008-03-05
I want to install Ubuntu on my new 160GB USB external drive, not the HD in my laptop. Is there a prompt I can use to force install to a drive other than my internal HD?
Maybe a Terminal invoked string?
Thx

UPDATE: This post is closed. I, with some great help here, managed to get Ubantu installed onto an external USB drive, correct the boot issues and am up and running at 99%. - THANKS TO ALL WHO HELPED !!

---

### Post by petzworld999 on 2008-03-05
During the install, it is easy to change the partitoner to install to an external hard drive. Under partitioning, go to 'manual' and follow the instructions. Be careful, though, if you are on a laptop machine, as I am, you will probably need your external hard drive plugged in to boot into any operating system, even Windows.

---

### Post by Ozzz on 2008-03-05
> **petzworld999 said:**
> During the install, it is easy to change the partitoner to install to an external hard drive. Under partitioning, go to 'manual' and follow the instructions. Be careful, though, if you are on a laptop machine, as I am, you will probably need your external hard drive plugged in to boot into any operating system, even Windows.

Thx Petz - I just noticed that 'manual' option and it selected the new WD USB HD. The drive is new and empty except for the files WD put on it. It is FAT32 also. The next screen, "Migrate Documents and Settings" is empty. (I am being very cautious here because I don't want to accidently wipe out my internal XP HD). It shows the external as SCS1

---

### Post by petzworld999 on 2008-03-05
You should be fine. The option to migrate just is an option to migrate your personal stuff from Windows, like documents, user name, password, etc. I was not there for me when I installed Ubuntu, and it did not mess me up one bit.

---

### Post by Ozzz on 2008-03-05
Thanks again. I ventured forward and it started to install - First time it sat at Installing System, Detecting file systems...  15% for about 8 minutes then the laptop just shut itself off. I am at that point again - waiting to see what happens this go around. 

I did have the options for Admin and me as user too.

EDIT: It sat there for 8-10 minutes again and laptop just powered off on me. BUMMER!

EDIT2: OK I see now in going to MANUAL my external is /dev/sda and /dev/sda1 (my internal should be the one labeled /dev/hda correct?). I need to setup partition table info - oh boy

Can someone give me advise on the partition settings for this drive: 160GB drive
1. I need a /root (mount point size) of at least 2GB
2. Swap partition of at least 256MB

What would these numbers be?

---

### Post by petzworld999 on 2008-03-06
I would recommend 10 GB minimum for Ubuntu, if you plan to use it often. If not, 8 should be fine. Set your swap to 512 MB, and install from there.

---

### Post by arashiko28 on 2008-03-06
Your home partition, will be where Ubuntu will be installed. The swap I recommend you to make it of the same size or double of your current RAM, this way it'll be easier to wake from hibernation or sleep.

Make your home partition of at least 10 GB so you have space to play around, if you plan saving stuff in it or your work, make it bigger. you're on the right track. Also, the sda1 is your windows partition. check the size before choosing one or the other so that there would be no mistakes, and of course, backup all your data before trying to do something like this for the first time.
Good luck and welcome to the Linux world, enjoy the freedom!:guitar:

---

### Post by Ozzz on 2008-03-07
Sorry at the delay in getting back here. I ran into a few snags and couldn't get my OS back.

Update to this point: I managed to get Ubuntu installed on my external USB 160GB drive for now. it was partitioned into two. Ubuntu installed on one of them.

In order to duel boot and get into my XP Pro I must have the external drive plugged in or I get Grub error 21. Not the best option for a laptop - i am guessing that my MBR has been changed. - [COLOR="Blue"]Is there a work around for this?[/COLOR]

When I was into Linux heavy five years ago I wasn't concerned with dual boot issies as everything was pure Linux. Now I am try to put it on my Toshiba A70 with a 60GB internal (XP using a bit less than half with all the stuff on it). I do not forsee adding anthing more to the XP side since I have all I need there. I figure I have 30GB if I partition for Ubuntu and the numbers are roughly: 10GB for mount point "/", 2GB for swap space, and the rest for "/home". I don't foresee adding many addins like tons of music or video as I keep those external.

I have an old Toshiba Tecra buried in the closet that is still set up with Win98 and Linux as dual boot and I don't recall it being so difficult to setup.

What is the best way to backup my XP partition, just in case?

UPDATE: This post is closed. I, with some great help here, managed to get Ubantu installed onto  an external USB drive, correct the boot issues and am up and running at 99%. - THANKS TO ALL WHO HELPED !!

---

### Post by petzworld999 on 2008-03-08
A good way to do so would be to make a disk image of your XP partition.

---

