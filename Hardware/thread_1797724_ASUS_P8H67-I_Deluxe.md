---
title: "ASUS P8H67-I Deluxe"
date: 2011-07-05
forum: Hardware
---

### Post by DimitrisC on 2011-07-05
I just purchased this motherboard from amazon in order to build a mini-itx pc!

[http://www.asus.com/Motherboards/Intel_Socket_1155/P8H67I_DELUXE/#specifications](http://www.asus.com/Motherboards/Intel_Socket_1155/P8H67I_DELUXE/#specifications)

I would really like to install ubuntu linux on this machine and I was wondering if anyone can offer some insight as to whether this motherboard works well with ubuntu (10.10 or 11.04).

Also can someone recommend a low profile graphics card to be used with this motherboard that also works with Ubuntu (I am using a Lian Li - PCQ07 case so space is kind of an issue when it comes to graphics cards).

Thank you.

---

### Post by chkeller on 2011-07-06
I've installed under P8H67-M Pro.
Problems:
(1) blank screen on boot. Solved with adding  nomodeset to grub file
(2) doesn't power down (still unsolved)
I use the iGPU (i3-2105).
See thread [http://ubuntuforums.org/showthread.php?t=1666626](http://ubuntuforums.org/showthread.php?t=1666626)

---

### Post by DimitrisC on 2011-07-06
From what I understand reading the thread you linked is that there is an issue with the new sandy bridge cpus and also the  integrated graphics.

Will the problem go away if I disable integrated graphics and use an external GPU?  I am not a big fan of the intel graphics anyway and I was thinking of purchasing an nvidia card.

---

