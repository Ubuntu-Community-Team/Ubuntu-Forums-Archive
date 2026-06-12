---
title: "Compiz and Nvidia"
date: 2008-01-19
forum: Hardware &amp; Laptops
---

### Post by lsutiger on 2008-01-19
I recently built a new desktop computer. I have the  EVGA 256-P2-N615-TX GeForce 7600GT video card. I have the restricted drivers enabled and I am running compiz. Running Gutsy.

I have a few little annoyances that I will list here:

When I have compiz running, I have this visible line between the top panel and the desktop. I have the  transparency set all the way for the panel. I saw this before on my laptop, but forgot how I got rid of it.

When I do a reboot, the shortcuts I placed on the panel disappear. When I try to put them back(grab the icon from the desktop and drag to the panel), the old shortcuts suddenly re-appear. 

Does anybody have the same video card with the same setup? Anyone having the same problems?

I have noticed some freaky deaky things also (such as the nvidia splash screen popping up outta nowhere after I log in), but I have not documented them all.

---

### Post by b0rka7a on 2008-01-19
> When I have compiz running, I have this visible line between the top panel and the desktop. I have the transparency set all the way for the panel. I saw this before on my laptop, but forgot how I got rid of it.
Do you mean the shadow of the panel ?
Go to ccsm > Window Decoration > Shadow windows:
change it from "any" to "any! &(type=dock)"

P.S: If you don't have ccsm installed, install it with
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by lsutiger on 2008-01-19
Thanx!

---

### Post by lsutiger on 2008-01-19
I am still having the problem between reboots. Attached are the files b4 and aft to show what I am talking about.

---

