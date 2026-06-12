---
title: "xserver issue"
date: 2005-12-27
forum: Hardware &amp; Laptops
---

### Post by lucprov on 2005-12-27
Just installed Ubuntu (breezy) Amd64 to Xp Machine with amd 4200X2, Asus AV8N-premium and Geforce 7800. The distro installed correctly without problems.  After booting, I get to the login and password prompt and then when I log in I get a brown screen . Whether I boot directly from the DVD or the hard drive I get the same result.
From the command prompt (recovery mode) I tried "sudo dpkg-reconfigure xserver-xorg"  but got "xserver not installed" message

I tried reinstalling but to no avail.  I downloaded another DVD version of Kubuntu to see if the problem would go away but nothing changed.

Any ideas.
P.S I'm new to linux

---

### Post by amohanty on 2005-12-28
In the recovery console try:

> sudo apt-get install xserver-xorg

Reboot.

HTH
AM

---

### Post by lucprov on 2005-12-28
It worked, I'm in

Thanks a lot

---

