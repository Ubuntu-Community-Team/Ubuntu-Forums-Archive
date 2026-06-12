---
title: "Installing Ubuntu on new laptop without deleting windows partition"
date: 2010-12-29
forum: Hardware
---

### Post by eljopc on 2010-12-29
I have a new Acer laptop that I want to use for Linux Ubuntu. The new laptop is Windows on a partition that has not been installed (hidden install\recovery PQSERVICE). I want to install Ubuntu without harming the windows hidden install partition so I can always install windows again from that partition.

How do I proceed?

Thanks for your help and thoughts.

---

### Post by Kirboosy on 2010-12-29
[COLOR=Red]Welcome to Ubuntu and the forms :D

[COLOR=Black]It is really quite simple actually. You just need to create a Ubuntu CD and insert it in your drive. Once the CD is ready shut down your computer and boot off of the CD.

Give it a few minutes to load

Once it loads fill out all the information accordingly. 

When it gets to drive partitioning just select 'Dual Boot'.

Drag the slider to determine how big you want the partition to be. Then hit next.



If that doesn't work you can the partitions manually. Scale down the Windows Partition and create an Ubuntu one. 

I would recommend that once you install Ubuntu that you do not install Windows behind it. If you think you will need Windows ever I would suggest installing it first. Windows wipes out Grub which will cause your computer to not boot Ubuntu anymore and its just a pain to fix.


~Caboose
[/COLOR][/COLOR]

---

### Post by eljopc on 2010-12-29
> **Caboose885 said:**
> [COLOR=Red]Welcome to Ubuntu and the forms :D

[COLOR=Black]It is really quite simple actually. You just need to create a Ubuntu CD and insert it in your drive. Once the CD is ready shut down your computer and boot off of the CD.

*** This I get.**

Give it a few minutes to load

Once it loads fill out all the information accordingly. 

When it gets to drive partitioning just select 'Dual Boot'.

***? Why dualboot, Windows Is not installed in the harddrive? (I think its an Iso in a separate partition.)**
[B]
* next question Is below explenation than stil correct?[/B]

Drag the slider to determine how big you want the partition to be. Then hit next.



If that doesn't work you can the partitions manually. Scale down the Windows Partition and create an Ubuntu one. 

I would recommend that once you install Ubuntu that you do not install Windows behind it. If you think you will need Windows ever I would suggest installing it first. Windows wipes out Grub which will cause your computer to not boot Ubuntu anymore and its just a pain to fix.


~Caboose
[/COLOR][/COLOR].

---

### Post by wilee-nilee on 2010-12-29
If you removed all of windows but the recovery I doubt it will be usable.

Take a screen shot of gparted on the booted live Ubuntu cd and post it.

---

### Post by Kirboosy on 2010-12-29
It is technically a "dualboot" but it really isn't. I was trying to show you the more GUI way. People get scared with the advanced partitioning. Like Wilee said it will be unusable after the install.

You can just tell Ubuntu to take the whole drive and if you ever need windows you can use virtualbox (unless you need it for gaming)

Or you just might have to install windows and fix everything it breaks after it installs.

If your computer has a recovery partition you might want to manual partition the drive and make sure Ubuntu doesn't wipe it out.

---

### Post by eljopc on 2010-12-30
Is it possible to,

**1** first run on boot the normal Win7 and install this on the laptop. 

**2** Than make the Acer recovery disks from Win7.

**3** than start Ubuntu from cd and start the install. 

**4** On partition delete the complete drive except the Acer hidden PQSERVICE partition.

*** **Ubuntu is now installed (I hope)

**5** When necessary boot With the Acer restore disks and restore Windows 7?

---

### Post by eljopc on 2010-12-30
Well today I received the laptop and pulled the hard-disk out before starting the laptop. I inserted an old hard-disk and started it up with an old Win 7 HP cd. If this works I do not need the hidden partition.

Update 1
It installs win7 with the serial code on the new laptop so I do not need the software on the hard-drive from the laptop. When I want to install windows I use the cd.

Now I'm testing still on the old HD if Ubuntu 10.10 works on this Acer

Update 2
Ubuntu 10.10 works out of the box on the Acer Aspire 5336-902G25MN
wifi [ok], sound [ok], what to test more?

---

