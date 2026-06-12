---
title: "How can I install NDISWRAPPER from CD?"
date: 2006-01-17
forum: Installation &amp; Upgrades
---

### Post by JimCockfield on 2006-01-17
Hello All!

I am a Linux Newbie and could use some help.

I'm considering trying an install of Ubunto 5.10 now.

I had previously avoided this distro, since NDISWRAPPER isn't included in the .iso, and I don't have a wired connection.

So, I've been sticking to trying out distros that have NDISWRAPPER there already (I need it for one of my cards).

Multimedia support is also a concern (but it looks like I may have found a solution for that part, if I use automatix.

Is there a way I can install Ubunto, then point it towards a CD containing a package for NDISWRAPPER (I don't want to figure out how to compile it from source)?

If so, what packages do I need, and where can I get them?

I see two directories related to NDISWRAPPER (ndiswrapper-modules-i386/ and ndiswrapper/) at this link (but I don't know what I need to download, or how to get it installed it from CD after an Ubunto install):

[http://archive.ubuntu.com/ubuntu/pool/universe/n/](http://archive.ubuntu.com/ubuntu/pool/universe/n/)

Any assistance at how to go about it would be appreciated.

Note that I know how to get NDISWRAPPER working (adding drivers, using modprobe, iwconfig, etc.), since I've been able to get it working in other distros I've tried.

I just don't know how to get it installed in Ubunto (since I don't have a wired connection and it's not on the install CD).

Thanks.

---

### Post by kaamos on 2006-01-17
Ndiswrapper should be in the installation cd, it is just not installed by default. Just type "sudo apt-get install ndiswrapper" when the system has booted.

---

### Post by az on 2006-01-17
Actually the module is on your harddrive and you just need the utility

sudo apt-get install ndiswrapper-utils

Or install it with synaptic.

It will work out-of-the-box.

You may need to get the very latest windows driver (inf file) since the one that come with your card may be too old for ndiswrapper.

---

### Post by JimCockfield on 2006-01-17
OK -- I'll install Ubunto and give it a shot.

I did try it from the Live CD, and it did not appear to be there.  I have not tried installing it from the "5.10 Install CD:" yet.

One web site with instructions said that it was only on the DVD and not on the CD version, so you'd need to compile it from source (so I assumed the info was accurate).  

I'll give it a try and see if it can find it or not.

---

### Post by JimCockfield on 2006-01-17
[QUOTE=azz]Actually the module is on your harddrive and you just need the utility

sudo apt-get install ndiswrapper-utils

Or install it with synaptic.

It will work out-of-the-box.

You may need to get the very latest windows driver (inf file) since the one that come with your card may be too old for ndiswrapper.[/QUOTE]

Thanks... I'm trying to use a Netgear WG311 Version 3 card.  I understand that Version 2 cards are supported.  But, unfortunately, Staples and other local vendors only had the Version 3 cards.   However, using the Win 2000 drivers works fine with NDISWRAPPER in distros like Kanotix 2005-04 and Mepis 3.4.2 RC1.  The only "quirk" is that you need to specify the ESSID (any/default won't work).

So, it will probably work OK in Ubunto, too, if I can get NDISWRAPPER installed.  I'm burning the 5.10 install .iso to CD now.  I'll let you know if it works OK or not.

Thanks again guys.

Jim C.

---

### Post by JimCockfield on 2006-01-17
It works fine guys (I was able to install ndiswrapper after an Ubuntu install by using sudo apt-get install ndiswrapper-utils )

I'm up and running with no problems using a Netgear WG311 Version 3 card with ndiswrapper.  I guess I should have tried it before asking.  LOL

Thanks again.

Jim C.

---

### Post by az on 2006-01-17
W00t!

---

