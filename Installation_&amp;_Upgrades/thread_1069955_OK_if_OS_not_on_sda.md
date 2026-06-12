---
title: "OK if OS not on sda?"
date: 2009-02-14
forum: Installation &amp; Upgrades
---

### Post by piblokto on 2009-02-14
Migrating a two-drive (both SATA) raid 1 array from one PC to another.  

I first installed 8.10 Server to the OS drive on the new PC.  That drive showed as 'sda' (e.g., boot partition was 'sda1').

I then hooked up the raid 1 array drives via a PCI-E adapter card, and the array automagically was detected.  However, the array drives now show as 'sda' and 'sdb' and my OS drive shows as 'sdc'.

First, is this a problem?  Things seem to work fine.

Second, is there a way to force the system to show the OS drive as 'sda'?

Probably doesn't matter, but in the BIOS of my PC the OS drive is listed first, with the array drives second and third.

---

### Post by Dies on 2009-02-14
> **piblokto said:**
> 
First, is this a problem? 

No. Linux doesn't really care where it's installed as long as fstab is correct. 

It might have caused problems if you were using device names in fstab, but this type of situation is exactly why most distros are now using UUID.

Though you might want to generate a new initrd if the new hardware is different.

---

