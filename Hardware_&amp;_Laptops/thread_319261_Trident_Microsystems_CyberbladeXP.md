---
title: "Trident Microsystems Cyberblade/XP"
date: 2006-12-15
forum: Hardware &amp; Laptops
---

### Post by bibstha on 2006-12-15
I have Trident Microsystems Cyberblade/XP 32 MB AGP graphics card - (very cheap i know:( ) but im not a hardcore games. I play games like old NFS porche, ...

I installed Torcs on Win XP and Ubuntu both but i get 25fps in Win XP while 1 frame per three seconds in Ubuntu, do u guys know what / who might be the culprit?

Regards
bibstha

---

### Post by tehdon on 2007-02-11
The culprit is the fact that there is no 3d accel for the cyberblade series card.  The only accel is very basic 2d.  You might try pulling the binary trident driver out of the most recent Debian unstable.  I've found that I get better performance from that driver versus the Ubuntu drivers.  You have to open the deb, manually extract the trident_drv.so file and overwrite the one in the /usr/lib/xorg/modules/drivers/  YMMV.

Actually, I'll attach the file so all you have to do is extract it.  Make sure you backup the old one, and also make sure you are using the trident driver in your xorg.conf.

Donald

---

### Post by BambooClaw on 2007-02-26
Thanks Tehdon, this worked great for me.  I have a Toshiba R100 with CyberbladeXP/4 chipset and was having all sorts of trouble with edgy.  Here's what I did:

Went to Debian Unstable Packages website
packages.debian.org/unstable/allpackages.html
Downloaded the xserver-xorg-video-trident.deb file from the xserver-xorg-video-trident package page
Extracted the trident_drv.so file from .deb with Archive Manager
Renamed the existing trident_drv.so in /usr/lib/xorg/modules/drivers/
Copied the new file to this location.
Restarted X

That's it, all working now, thanks.

---

### Post by matthewboh on 2007-03-06
I've been searching for a fix for the scrolling up error on my Toshiba M1 with the Trident XP4m32 card, and this fixed everything.  Thanks!

---

### Post by PooingCavy on 2007-05-29
Hello, is there a safe risk free way to install a driver. As in fool proof, theres no way to go wrong.

---

### Post by PooingCavy on 2007-05-29
bump

---

### Post by PooingCavy on 2007-05-29
how do i install this!

---

### Post by PooingCavy on 2007-05-31
[http://youtube.com/watch?v=oEi6pC2NSJk](http://youtube.com/watch?v=oEi6pC2NSJk)

this is my problem.

HELP!

---

### Post by imot on 2008-05-15
i have done anything, but The Dekstop Effect on my Satellite a25-s207 still dosn't work. how can i do for make it work better?please help me. 
i'm running on Ubuntu Gutsy Gibbon.

---

