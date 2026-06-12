---
title: "Server 2008 x64 BOOTMGR is missing"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by bharat9 on 2009-07-09
Hardware Specs:
Laptop; Core2Duo P8400, 320GB HDD (partitioned as shown below), 4GB RAM.

Software:
Partition 1 (200GB): Windows Server 2008 Standard x64 on (NTFS)
Partition 2 (120GB): Kubuntu 9.04 x86 (EXT4)

Problem:
Cannot boot to Windows.

Kubuntu did not even detect my Server2008 installation. I manually added the lines for my Windows partition as shown below:
```
title 		Windows Server 2008 Standard
rootnoverify 	(hd0,0)
makeactive
chainloader 	+1
```
 but then it still gives me the error "BOOTMGR is missing. Press Ctrl+Alt+Del to restart."

I tried Windows Startup Recovery options including the usual bootrec commands, but they don't work. I first tried "bootrec /rebuildbcd" (where it found the windows installation in C:) and then "bootrec /fixboot" and then tried to restart, but it didn't work.

I tried to remove/format the Kubuntu partition from the (Windows) recovery console command prompt, but (understandably) the EXT4 partition was not even visible.

**I want to uninstall Kubuntu in a way that my Windows partition then resumes its normal operations.**

Please help, my behind is on the line here! :/ No more stupid experiments for me, that's for sure.

---

### Post by bharat9 on 2009-07-09
Now I tried "bootrec /fixmbr", and I can't see the Ubuntu grub selection screen! **HELP!** :-k

---

### Post by bharat9 on 2009-07-10
Anyone?!

---

### Post by Gojulas895 on 2009-07-22
...

---

