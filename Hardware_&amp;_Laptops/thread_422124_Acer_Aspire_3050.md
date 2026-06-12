---
title: "Acer Aspire 3050"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by govi on 2007-04-24
The wireless doesn't work, the driver is ok, but can not find the AP. 
Under the skype, the mic doesn't work. I can here the sound in system but in skype.

---

### Post by kerry_s on 2007-04-24
Install ndisgtk and use the windows driver.(sudo-apt-get install ndisgtk)

click on the volume icon and turn them all on and up.

I have the same laptop, your also going to want qsynaptics or gsynaptics for the touch pad control.

---

### Post by govi on 2007-04-24
the touchpad is ok. 
the other problems are web camera  and wireless

---

### Post by kerry_s on 2007-04-24
I don't have a web cam, so can't help there.

The ndisgtk is a wrapper for the windows wireless driver zdxx.ini that's what i used to use till mine died.

The touchpad thing is for better control, i use qsynaptics and have it setup for 1 finger,2 finger and 3 finger tapping as well as scrolling.

---

### Post by mississippifawn on 2007-06-12
I am having trouble getting the sound to work on my new Acer Aspire 3050, any advice would be helpful

---

### Post by Guilden_NL on 2007-06-16
Ditto, I am working on it.  I'll post back here once I figure out a solution.  Everything else works perfectly!  \\:D/

---

### Post by carlao2005 on 2007-07-05
Hello Kerry_s (and all friends),

A friend of mine bought this notebook (aspire 3050-1458). It came with linpus linux. I have erased it and installed ubuntu 7.04. Everything worked fine (even the sound, it was just a matter of turning on the "surrond"), except the network.

We have tested at out university, where there is DHCP. With my notebook (hp pavilion dv6120), I have just to plug the cable, and it's on the net. This acer, no way...

I have tested at home, where I have an adsl connection. With my hp, it was just a matter of using "pppoeconf", and after 12 seconds it was connected. This acer, when I use pppoeconf it says that found eth0 (and even eth1 !!), but did not find any adsl modem.

The command lspci says it has a realtek network card.

Do you have any hint?

Best regards!
Carlos

---

### Post by a30d on 2007-09-04
> **Guilden_NL said:**
> Ditto, I am working on it.  I'll post back here once I figure out a solution.  Everything else works perfectly!  \\:D/

This worked for me everyone... this post is from rob-acer:

> Anyway, I found the fix at: [http://nosrednaekim.wordpress.com/2007/05/28/linux-on-the-acer-aspire-5050/](http://nosrednaekim.wordpress.com/2007/05/28/linux-on-the-acer-aspire-5050/).

I added two lines to the end of the alsa-base file using sudo gedit. This file is located in /etc/modprobe.d/alsa-base. Here are the two lines:

alias snd-card-0 snd-hda-intel
options snd-hda-intel index=0 probe_mask=3 position_fix=3


Hope it works,

Bryan

---

### Post by pythonweb on 2007-12-05
Hello All:

   I'm trying to install KUbuntu on an Aspire 3050-1066 with no luck at all. The KUbuntu Live CD will boot to the desktop, clicking on the install was smooth and everything seemed fine, but on reboot all I get is an error saying something about not being able to get a PCI resource; it says something about a PCI_BRIDGE error then the screen goes blank. the error is only shown for a fraction of a second, so I don't have the exact error.. I'd really appreciate help, I refuse to be held captive by Winblows when there's a lovely and capable OS like Ubuntu :)

Note that there was no indication of a problem during installation that I noticed. 

Peace!
Jon.

---

### Post by Stupid_newbie on 2008-06-19
> **pythonweb said:**
> Hello All:

   I'm trying to install KUbuntu on an Aspire 3050-1066 with no luck at all. The KUbuntu Live CD will boot to the desktop, clicking on the install was smooth and everything seemed fine, but on reboot all I get is an error saying something about not being able to get a PCI resource; it says something about a PCI_BRIDGE error then the screen goes blank. the error is only shown for a fraction of a second, so I don't have the exact error.. I'd really appreciate help, I refuse to be held captive by Winblows when there's a lovely and capable OS like Ubuntu :)

Note that there was no indication of a problem during installation that I noticed. 

Peace!
Jon.

My sound card works ok (only through Earphones but I can live with that)

as for the issue of the installation, you need to upgrade your BIOS. there is a FLASHBIOS program that works with Windows (it says VISTA but it will work with XP)  you then neeed to re-install UBUNTU. Hope that works.

---

