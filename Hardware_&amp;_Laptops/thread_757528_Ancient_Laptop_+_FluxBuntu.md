---
title: "Ancient Laptop + FluxBuntu"
date: 2008-04-17
forum: Hardware &amp; Laptops
---

### Post by TheMemphisExperience on 2008-04-17
I have a colleague that is giving an old Dell Inspiron(built for Win 98, presently running XP) to some friend of hers. I wanted to put Ubuntu on it, but thought even Xubuntu would be too much for it. But if it can do XP, it should be able to do XUbuntu, which is still an option. Anyway, I wanted to try out the FluxBuntu live CD, but got so far into a series of menus, I thought it was actually going to install itself.

Has anyone used FluxBuntu's liveCD? Should I just use Xubuntu and hope for the best?

---

### Post by beckejc on 2008-04-17
I am very close to giving up on Fluxbuntu.  The alternate install fails every time I run it.  It craps out during the "Install Base System" step with some error about setting up /dev failed.

I have found no mention of this on the web.  I ran a checksum on it, as well as the CD check on the install CD and both were OK.

Too bad, since by the looks of it, it would be great on 3 old computers I have.

I went ahead and installed Xubuntu which is very pretty and seems to be working.  It is much "thicker" than Fluxbuntu (at least according to reports), but may be OK.

---

### Post by kerry_s on 2008-04-17
if you don't put spec's we can only guess.

here is the standard run down->

0->64mb ram = DSL
[http://damnsmalllinux.org/](http://damnsmalllinux.org/)

128->256mb ram = xfce4, preferably not ubuntu version, it's slow, debian is great
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-xfce-CD-1.iso)

256->1gig ram = anything you want your good to go

---

### Post by LeoSolaris on 2008-04-17
You could also try Puppy, and put Fluxbox on it rather than it's current WM. I have seen it done more than a few times in their forums, though to be honest, for the lighter WM's FVWM-Crystal is one of the prettier ones.

I may have to take a peek at the Deb-Xfce out of pure curiosity though.

Leo

---

### Post by beckejc on 2008-04-17
I just happened to run across this on the net:

The FluxBuntu install will not work if you are setting up LVM via the install.  You have to abandon LVM until after the install is complete (use hard, physical partitions).

I presume LVM can be set up after the install, but I haven't tried it yet.

---

