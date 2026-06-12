---
title: "Ubuntu power management too simple"
date: 2007-06-02
forum: Hardware &amp; Laptops
---

### Post by fboecom on 2007-06-02
After some weeks of trying to get Ubuntu working on the VIA EPIA EN I finally succeeded, reasonably happy, but this thing meant as server - just doesn't do power management well. In ubuntu I only have the option suspend and hibernate. Suspend powers down Ubuntu to a state where it asks me 'Please Halt me manually'. 
Windows2000 does a decent job in being able to power down the monitor, then the disk, the the system in standby, then the system in sleep. This works all so well, out of the box, that I think I will return to Windows for this single reason.

Any thoughts? My platform is VIA EPIA-EN (1.5Ghz), Ubuntu 7.04, dual boot W2k/ubuntu.

Freek

---

### Post by NilsE on 2007-06-02
Have you experimented at all with the PM  options in the Configuration Editor under apps/Gnome-Power-Manager? Not elegant but there is a lot of options in there.

I actually turned off all power saving options in both XP and Ubuntu and get about 10 minutes more battery life in Ubuntu.

---

### Post by fboecom on 2007-06-03
I don't have that application, that may be the reason?

Freek

---

### Post by NilsE on 2007-06-03
> **fboecom said:**
> I don't have that application, that may be the reason?

Freek
Go into the panel "System/Preferences/Main Menu/System Tools" and check it then you will have it.

---

### Post by fboecom on 2007-06-04
Thanks, Nils, but it is not there.
Would there be any realtionship with installing Ubuntu as Desktop or Laptop (Mine is Desktop, but I want the power managmeent)

---

### Post by NilsE on 2007-07-08
> **fboecom said:**
> Thanks, Nils, but it is not there.
Would there be any realtionship with installing Ubuntu as Desktop or Laptop (Mine is Desktop, but I want the power managmeent)
You may need to go into main menu or menu editor and add it since it may not be selected by default.

If that does not work go into a terminal and type 

gksudo gconf-editor

---

