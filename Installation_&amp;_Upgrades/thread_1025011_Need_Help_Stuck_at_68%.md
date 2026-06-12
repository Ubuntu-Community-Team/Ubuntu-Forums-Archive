---
title: "Need Help Stuck at 68%"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by TraceurJ on 2008-12-29
Hi, I am trying to install Xbuntu(As the only OS) on my laptop. And it seems that it is always stuck on 68% and not moving the mouse stops working. What could cause that? and How do I fix it?

---

### Post by Partyboi2 on 2008-12-29
Did you check the cd for defects before trying to install? What are you systems specs?

---

### Post by Partyboi2 on 2008-12-29
Deleted.

---

### Post by Coreigh on 2008-12-29
You don't say if this an older laptop, but that is usually the case. I have had problems with the ACPI features (power management) Also having too little memory (RAM) can hang an install. Does the LiveCD work normally butthe install fails or have you not tried the LiveCD?

You can work around the ACPI issue by choosing custom boot options at thestarup menu (F6 I think), add "ACPI=off, NOAPIC" [without quotes] to the boot options. This turns off some power management features that don't have good compatibility with older hardware.

The memory issue; of course add memory is one option. But another is to use the "Alternate Install" CD, it has lower hardware requirements. Or install Ubuntu Server and add a "lightweight" graphical manager like icewm.
```
sudo apt-get install icewm xdm numlockx xterm xserver-xorg-core xfonts-base
```
That last option does not offer all the ease and convenience of the full Xubuntu desktop though.

---

### Post by TraceurJ on 2008-12-29
Ya, it works when i run it Live it works perfectly but not when i try to install

---

### Post by AeroTITAN on 2008-12-29
Are you connected to the internet during the install?  I had a problem where the install hung for three hours because it was searching for updates during the install, yet I wasn't online.

---

### Post by linux_tech on 2008-12-29
Suggestion 1- Try alternate cd install.
[http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.10/release/](http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.10/release/)
select correct version depending on your system 
PC (Intel x86) alternate install CD
    For almost all PCs. This includes most machines with Intel/AMD/etc type processors and almost all computers that run Microsoft Windows, as well as newer Apple Macintosh systems based on Intel processors. Choose this if you are at all unsure.
64-bit PC (AMD64) alternate install CD 

Burn new iso and try to install.

Suggestion 2- If alternate does not install, then pre-format partition w/ ext3.
You can use gparted off live cd to do this.

---

