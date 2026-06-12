---
title: "Hibernation on ASUS Eee 1000HA"
date: 2009-01-14
forum: Hardware
---

### Post by majukutaj on 2009-01-14
I've searched the forums and tried everything I could find...
 
I'm running Intrepid on an ASUS Eee 1000HA.  When I attempt to shut down, the only options offered are "Shut Down", "Restart", and "Suspend".  These, including suspend, all work as expected.
 
I have 2GB RAM, and a 4GB swap partition. (old habits...)
 
In gconf, /apps/gnome-power-manager/general, I have "can_hibernate" and "can_suspend" set to true.
 
In /etc/default/acpi-support, I have 
ACPI_SLEEP=true
ACPI_HIBERNATE=true

I'm dual-booting XP, and keep an unused partition for playing around, separate /home, and so on, which leads to eight partitions; do I have to explicitly specify the swap partition to use for hibernation somewhere?  
 
Does anyone have any ideas?  Thanks!

---

