---
title: "Install on intel 133"
date: 2006-01-09
forum: Installation &amp; Upgrades
---

### Post by [Nirvana] on 2006-01-09
I want to install the ubuntu-server (base install) on an old intel 133, and then 
```
sudo apt-get install fluxbox x-window-system-core xdm dillo synaptic
```
(which I got from the wiki) to install a lightweight system. Basically, I want something like DSL, but I don't want DSL (I tried it, too many broken deps, it's a pain in my ass). 

**_Problems I've had:_**
This computer, because it is very old, can not boot from CD. I've read this wiki [ [https://wiki.ubuntu.com/SmartBootManagerHowto](https://wiki.ubuntu.com/SmartBootManagerHowto) ], but neither SmartBoot managers (the d/l'd one and the one in the install directory of my Kubuntu CD) work. They give me an error (0x01). I have the Kubuntu Breezy CD, and there is nothing wrong with it. How can I get the Ubuntu install process started?

-I can't open up the box
-I can't boot from CD
-I can use instlux, because I have a 98SE startup disk, and the 98SE install disk, but I don't know how instlux works, so I would need a guide.
-I'd really just like a nice, simple boot disk, like DSL's boot disk (would it work for booting up the Kubuntu CD?) that would make it so I can install ubuntu-server

I prolly searched the wiki about 100000 times, and tried it myself, and would like it if a third party could help me... because I myself am a Linux beginner (been using Kubuntu since Haloween)

Please don't tell me to go back to DSL, there is too many problems, and I really appreciate the locks of hair I still have on my head...

---

### Post by Sef on 2006-01-09
Had a computer that would not take a debian install; finally got vector linux on it.  Vector is based on slak.   See if that works for you.

---

### Post by [Nirvana] on 2006-01-09
It's not that I can't install it I don't think, I think it's just me having bad luck with boot disks.

Also, I looked at vectorlinux.com, it seems cool, but it takes up too much space (950 MB, the HDD is only 2GB). But in the event that I do try it, what is the package manager? I'm really comfortable with debs, but it looks like slackware has it's own PM. I'll use this as a backup, but I'd really like to get Ubuntu-server on it.

Thanks though :D

Edit: In the event that I do install it, is it possible to do a base install? I know OOo, and GIMP prolly won't run on the comp, so I wouldn't want them. Also, what is the command for it's pkg manager?

---

### Post by Sef on 2006-01-09
The package manager is Gslapt.

---

### Post by [Nirvana] on 2006-01-09
[QUOTE=Sef]The package manager is Gslapt.[/QUOTE]

Is it like apt? Such as slapt-get install, slapt-get remove, slapt-cache search.

Also, anyone else know what I can do for the Ubuntu-Server install? I really would prefer it over slackware, I don't know why, but Ubuntu is just so... cuddly :razz:

---

### Post by christhemonkey on 2006-01-09
You could try doing what i did:
[http://ubuntuforums.org/showthread.php?t=114868]("http://ubuntuforums.org/showthread.php?t=114868")

---

### Post by [Nirvana] on 2006-01-09
[QUOTE=christhemonkey]You could try doing what i did:
[http://ubuntuforums.org/showthread.php?t=114868]("http://ubuntuforums.org/showthread.php?t=114868")[/QUOTE]
I did, and I just tried again, and I can confirm that it is the disk image that is the problem. Anyone know where I can get a diff image?

---

### Post by christhemonkey on 2006-01-09
Off the official site?:
[http://ubuntu.hands.com/releases/5.10/ubuntu-5.10-install-i386.iso]("http://ubuntu.hands.com/releases/5.10/ubuntu-5.10-install-i386.iso")

---

### Post by [Nirvana] on 2006-01-09
[QUOTE=christhemonkey]Off the official site?:
[http://ubuntu.hands.com/releases/5.10/ubuntu-5.10-install-i386.iso]("http://ubuntu.hands.com/releases/5.10/ubuntu-5.10-install-i386.iso")[/QUOTE]
Yep, right from the /install folder :P

I just tried a [net install]("http://www.ubuntuforums.org/showthread.php?t=75372&highlight=netinstall"), and aside from it being next to impossible to find 5 floppy's that still work in my house, I got it running. Slight problem after it loads all the floppies though. It gives me a "kernel panic". It says something like:
```
free swap: 0k
used swap: 0k
Out of Memory: Killed process 755 (cp)
kernel panic - not syncing, attempted to kill init

```

Now, this makes me mad not only because it took me half an hour to find floppies, but because my swap partition is on THE FIRST PARTITION OF THE DRIVE (weird, I guess it forgot to look there...). Is there any way to make it recognize the swap partition. I made it with cfdisk, so it should be OK, right?

Also, I seem to having reading problems. The computer is an intell 166. and I know it's giving me Out of Memory errors because I have only 32MB/RAM, but that's what the swap is for! Too bad it can't read the swap, eh?

Any more helpful tips anyone can give?

---

