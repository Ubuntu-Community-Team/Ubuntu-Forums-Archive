---
title: "Ubuntu as 3rd operating System"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by grump21 on 2009-09-07
I am running WinXPPro and Windows7 on my 1st hard drive and have a dual boot menu.

If I install Ubuntu 9.04 in a 3rd partition what will Grub do to my dual boot menu and how will it look.

I would very much like to use Ubuntu but would still like Windows to be available for running Photoshop and MSMoney.

John

---

### Post by ebmelle on 2009-09-07
Grub should give you a choice of Ubuntu or Other (Windows), that may go to a new window, XP or Vista/(win 7).

Once logged in to Ubuntu you can go to terminal and edit menu.lst in /boot/grub to change the default OS to you liking.  the command line will be something like;
    sudo gedit /boot/grub/menu.lst
 respond with your super-user password, and the text of the menu.lst will appear ready for editing.  Read instructions carefully!

---

### Post by presence1960 on 2009-09-08
GRUB will be installed to MBR and will take over when you boot. You can edit or add the windows entries from within Ubuntu.  

GRUB will present you with the list of OS's on your machine that you can choose to boot.

GRUB is very configurable and you can select which OS is the default. You can also select how long of a delay before the default OS boots if you select nothing.

As long as you have the windows install disk or [Super Grub Disk]("http://stmaarten.globat.com/~supergrubdisk.org/") you can always restore windows to MBR if you wish.

I run 4 OSs. Ubuntu 9.04, Sabayon 4.1, Crunchbang 9.04 and Windows. GRUB works like a charm!

---

### Post by grump21 on 2009-09-08
Thanks for your replies.

I now feel more confident.

---

### Post by presence1960 on 2009-09-08
> **grump21 said:**
> Thanks for your replies.

I now feel more confident.

If you need help configuring GRUB post back.

---

