---
title: "Grub error ALERT! /dev/hda1 does not exist"
date: 2009-06-25
forum: Installation &amp; Upgrades
---

### Post by zach_delta on 2009-06-25
Over the last weekend I upgraded my ubunto system from Ubuntu 6  to Ubuntu 8. This included going from kernel kernel 2.6.15 to 2.6.24.    After the upgrade had completed and when I attempted to reboot grub gave an error 
“ALERT! /dev/hda1 does not exist.  Dropping to shell”.
Fortunately I was to boot with the old kernel.  

To cut 3 shorts days of investigation short I found:
After the upgrade IDE devices are now identified as SCSI devices also.  IE /dev/hd?? no longer exist they are now all /dev/sd??  

THIS HAD NOTHING TO DO WITH MY PROBLEM.  
My problem was that after the upgrade I could no longer specify in menu.lst  

“kernel /boot/vmlinuz-2.6.24-24-386 root=/dev/hda1 ro quiet splash noapic”  

I had to specify it as  
"kernel /boot/vmlinuz-2.6.24-24-386  root=UUID=<IUID Number> ro quiet splash noapic”  

The weird thing was that the upgrade process had upgraded /etc/fstab so I was able to extract the UUID number from it. 

Hopefully this may be of use to someone else.
Cheers zach

---

### Post by jimv on 2009-06-25
> **zach_delta said:**
> 
To cut 3 shorts days of investigation short I found:
After the upgrade IDE devices are now identified as SCSI devices also.  IE /dev/hd?? no longer exist they are now all /dev/sd??  

THIS HAD NOTHING TO DO WITH MY PROBLEM.  


Actually, that had everything to do with your problem.  /dev/hda1 no longer existed (due to driver differences between 6 and 8 ).  If you had replaced hda with sda in your menu.lst, you would have been fine too.

---

### Post by zach_delta on 2009-06-26
Jimv,

I stand corrected.  When I tried that it, by itself, it worked.

I know I had tried that earlier, but have a lesser understanding of GRUB than I do now, I had similtaneously updated the line "root (hd0,0)" to "root (sda,0)" or "root (sd0,0)".

I had presumed if one changed from HDxx to SDxx the other also changed to SDx.  

I know, sigh, realise this is not the case.

Cheers Zach.
	s

---

### Post by presence1960 on 2009-06-26
live and learn like the rest of us. it's all good!

---

