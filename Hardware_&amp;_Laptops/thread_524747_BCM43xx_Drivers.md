---
title: "BCM43xx Drivers"
date: 2007-08-13
forum: Hardware &amp; Laptops
---

### Post by rock lobster on 2007-08-13
So I came across this wicked awesome setup guide for the bcm43xx wifi drivers [http://ubuntuforums.org/showthread.php?t=405990]("http://ubuntuforums.org/showthread.php?t=405990")

This helped me greatly but the only problem I am having is that the when I go home and I lose connection every 20mins, then I have to restart. Also it goes crazy slow sometimes like 1-7kbps, and I might be mistaken but after installing this firmware does it only operate in B mode? Anyway if anyone has any methods of optimizing these drivers that would be awesome.

---

### Post by ugm6hr on 2007-08-13
I don't have a Broadcom (thankfully).  But this is a common debate - ndiswrapper or fwcutter for BCM43xx

This link is useful: [http://bcm43xx.berlios.de/?go=devices](http://bcm43xx.berlios.de/?go=devices)

It lists which chipsets are unstable with fwcutter - I suspect yours is one of them.

And fwcutter will not go beyond 11Mbps (i.e. b, not g).  ndiswrapper will give you 54.

But... fwcutter - easy.... ndiswrapper - slightly less easy.

---

### Post by rock lobster on 2007-08-13
I used ndiswrapper before but now that i have 7.04 it doesnt seem to work anymore for some reason.

---

### Post by srt4play on 2007-08-13
I take care of three laptops that have broadcom wireless and use ndiswrapper on all of them.  I never use bcm43xx because of the reasons you state in your first post, but mainly because speed is capped to 11Mb. 

Download the ndiswrapper source package from ndiswrapper.sourceforge.net.  It's really easy to set up.

---

### Post by jml on 2007-08-13
Since you have the Broadcom drivers installed, you will have to blacklist it in order for the Windows driver plus ndiswrapper to work.  Otherwise the two will coflict and you will have no wireless.  Search this forum for the terms blacklist and Broadcom, and you should find the appropriate steps to take.  Good luck.

Joe

---

### Post by rock lobster on 2007-08-13
OK i will try blacklisting the broadcom drivers i know how to do that, would I be able to pull that from apt-get? or is it just better from sourceforge?

---

### Post by srt4play on 2007-09-06
You can pull it from apt-get, but some broadcom chips require a newer version of ndiswrapper than what you get via apt-get.

---

