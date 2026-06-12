---
title: "Removing Ubuntu"
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by Allyhibs on 2009-04-17
Seems to be very little information about how to do this so I thought I'd ask here. I installed Ubuntu by dual booting with XP and partitioning my hard drive. I'd now like to remove Ubuntu and recover the hard drive space for XP, how do I go about this?

---

### Post by Carl Hamlin on 2009-04-17
> **Allyhibs said:**
> Seems to be very little information about how to do this so I thought I'd ask here. I installed Ubuntu by dual booting with XP and partitioning my hard drive. I'd now like to remove Ubuntu and recover the hard drive space for XP, how do I go about this?

The quick and dirty way would be to format the Ubuntu partition as an NTFS volume from within Windows, but that still leaves GRUB on your system. I'm not sure that there *is* a defined way to remove Ubuntu seamlessly.

---

### Post by Flareside on 2009-04-17
Format the partition as NTFS from windows just like the previous post said, and then boot with the XP disk in an select reapair. You should get a command prompt and then i believe the command is "fixmbr", which will remove the grub loader and stop it from giving you an error every time you turn on the computer.

---

