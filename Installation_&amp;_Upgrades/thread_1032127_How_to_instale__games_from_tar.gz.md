---
title: "How to instale  games from tar.gz"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by Gunch36 on 2009-01-06
so i try to install Railroad Tycoon II on my UBUNTU 8.10, but i dont know how to do that. The README file says:
> Mount the Railroad Tycoon II CD and change the current directory
to where it is mounted.  Type 'sh setup.sh' to run the install script.

e.g.  Log in as root:
	mount /mnt/cdrom
	cd /mnt/cdrom
	sh setup.sh
could some one explain  please what do i do whit it... first how do i mount it (ARCHIVE Mounter I guess). and what  does > change the current directory
to where it is mounted mean ????? :confused:
where do i tipe 'sh setup.sh'??? 
and im fully blind also about mount > /mnt/cdrom
	cd /mnt/cdrom
	sh setup.sh
could some on help me please??? [-o<

---

### Post by Tim Sharitt on 2009-01-06
Ubuntu probably mounted the CD when it was put in (unless you have disabled auto mount), so I am going to skip the mounting step.
Open a terminal by going to the Applications menu > Accessories > Terminal. Once it is open enter:
```
 cd /media/cdrom
sh setup.sh
```
If any of those steps cause an error repost them here.

Edit I just noticed the thread title. Are you trying to install from a tar.gz file or a cdrom?

---

### Post by paris_alex on 2009-01-06
if your Ubuntu desktop automatically mounts the CD (default behavior), then you might be able to just explore to the CD directory (using nautilus, the file manager) and double click on the setup.sh file.

if you're asked what to do, say 'i want to run or execute this file'...

hope this helps.

---

### Post by paris_alex on 2009-01-06
oh.. forgot to add.. i used to love railroad tycoon back in the DOS days! ;-)

---

### Post by Gunch36 on 2009-08-08
guntars@gunch-laptop:/media/cdrom$ sh setup.sh
sh: Can't open setup.sh

what next?

---

### Post by UN|X on 2009-08-08
[SIZE="4"]Take a look at this Youtube tutorial [Video 5 - Installing and Removing Software in Ubuntu - LINUX]("http://113663ee.*********.com")
Follow the link to the tutorial video. I had some real bad trouble understanding this when I first started. Video will clear things up a bit.
[/SIZE]

---

### Post by Gunch36 on 2009-08-08
yeah.. thank You, but i know how to use the synaptic package manager... that doese not solve my problem.

---

### Post by Gunch36 on 2009-08-09
could someone help me please?

---

### Post by KinaU on 2009-08-09
[http://ubuntuforums.org/showthread.php?t=297978](http://ubuntuforums.org/showthread.php?t=297978) 

This might help you. :)

Edit: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) 

A how-to for compiling.

---

### Post by Partyboi2 on 2009-08-09
> **Gunch36 said:**
> guntars@gunch-laptop:/media/cdrom$ sh setup.sh
sh: Can't open setup.sh

what next?
Hi, as Tim Sharitt mentioned are you trying to install from cdrom or tar.gz (let us know so we can provide better help)? If its a tar.gz then you will need to extract it and enter the source directory.
The above message you are getting is probably because there is no setup.sh in the cdrom directory. If you have the  Railroad Tycoon II cd make sure it is in the cdrom.

---

