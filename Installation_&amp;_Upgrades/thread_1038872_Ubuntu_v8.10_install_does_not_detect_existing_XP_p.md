---
title: "Ubuntu v8.10 install does not detect existing XP partition/drive"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by monikersupreme on 2009-01-14
I am attempting to set up a dual boot workstation with Ubuntu v8.10 and Windows XP Pro (with XP already installed). I have two 250GB drives, the former already has a working XP installation and the latter on to which I intend to install Ubuntu.

I'm following the procedure on the following site:

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

Everything was going smoothly until my Ubuntu installation died ~35% of the way through due to a corrupt install CD. I canceled the installation, booted back into XP, re-formatted the drive (on which I'd just attempted to install Ubuntu), burned a 2nd Ubuntu installation CD and attempted to install again...

When I ran the installation CD again I notice that the Ubuntu installer did not "see" the XP partition/drive as it did in my previous attempt and I'm concerned that GRUB will not be configured correctly to recognize the XP partition (and provide me with the option of either installation) if I allow the installation to complete... 

Is this something I need to be worried about - how do I get the installation CD to recognize the XP installation on the adjacent drive? 

Any advice would be much appreciated... 

Thanks!

( BTW, ignore my sig - those details are for my laptop installation, my current specs are:
MSI K9MM-V / 2GB DDR2 / AM2 5200+
TrendNet Wireless-N PCI card
BFG 7800GS AGP card
2 x 250GB Hitachi SATA150 drives )

---

### Post by kranny on 2009-01-14
Boot into ubuntu and fire up a terminal to open device.map in the grub folder

```
sudo gedit /boot/grub/device.map
```
you will find something like 
```
(hd0)	/dev/sda
(hd1)   /dev/sdb
```

Just map the same in your menu.lst like this if you are having xp in you second 250gb drive

```
sudo gedit /boot/grub/menu.lst
```
title        Windows Xp
root        (hd1,0)
savedefault
makeactive
[B]map        (hd0) (hd1)
map        (hd1) (hd0)[/B]
chainloader    +1

---

### Post by monikersupreme on 2009-01-14
Thanks for the response.

I haven't installed Ubuntu yet; what puzzles me is why, when I boot into Ubuntu using the install CD, it no longer recognizes the XP partition sitting on the latter drive, especially since I re-formatted the former drive that I initially tried to install Ubuntu on (after my install attempt failed). 

**When you say "Boot into ubuntu" do you mean using the v8.10 install CD?**

I thought perhaps that during my first abortive install attempt I might have corrupted the MBR of my XP installation, but if that were so I doubt XP would still boot...

**If I attempt your instructions will I still be able to import my XP settings / configurations during the Ubuntu install process?**

---

### Post by kranny on 2009-01-14
use any live cd for that matter
> If I attempt your instructions will I still be able to import my XP settings / configurations during the Ubuntu install process?

Yes Definitely

---

