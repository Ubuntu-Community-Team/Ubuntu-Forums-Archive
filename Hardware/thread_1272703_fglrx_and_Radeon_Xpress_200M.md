---
title: "fglrx and Radeon Xpress 200M"
date: 2009-09-22
forum: Hardware
---

### Post by Meetze on 2009-09-22
I've spent a lot of time scouring the Internet and trying different things to get flgrx to recognized and use my Radeon Xpress 200M on my Averatec 7100.  Ubuntu 9.04 has a default wrapper that helps with Xorg.  However, most 3D applications are slow or don't work at all (Segment Fault Errors).

I would like to get flgrx up and running since it does support the Xpress series.  I have been unable to find any directions that actually work.

It's strange really.  The Hardware Drivers app doesn't even recognize that I have an ATI card.

Any suggestions?

---

### Post by Meetze on 2009-09-22
Hey, I found something that really worked!

Dump Jaunty - Installed Intrepid

Makes sense really.  If I want a newer version of the OS, then I probably need a newer computer.  Too bad really.  Jaunty was looking very good and ran well on my machine.

---

### Post by Kryzzalid on 2009-09-27
Hi,

I also have an ATI radeon xpress 200M 128/256mb on my laptop. And I have as well problems with the 3D applications like video games. I tried lately to get to work Half-life 2 on wine. The game runs but it's extremely slow even on the lowest configuration! I tried to install those ATI divers found from their website (they are supposed to work with my video card) but i got the following message:

==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-15-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.zxzHRF

The package is ati-driver-installer-9-3-x86.x86_64.run.
Does anyone know how i could fix that? Thanks:)

---

### Post by benmoran on 2009-09-27
ATI dropped support for the older cards in FGLRX. The open source drivers are slower for some things (like 3d intensive stuff), but are better in a lot of ways. They are quickly catching up in support. Give it time. 

I've been using the open source drivers for about 6 months now, since I don't want to be stuck with Intrepid. FGLRX was always buggy as hell anyway. The open source drivers are getting better every month.

---

### Post by Kryzzalid on 2009-09-28
Which ones are the open source drivers for ATI?

---

