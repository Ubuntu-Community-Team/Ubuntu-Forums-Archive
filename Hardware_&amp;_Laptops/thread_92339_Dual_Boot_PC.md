---
title: "Dual Boot PC"
date: 2005-11-19
forum: Hardware &amp; Laptops
---

### Post by BadHead on 2005-11-19
Hi,

I am new to Ubuntu, althought I have used a onux distro before, and wish to install Breezy Badger onto my PC to run along-side my Windows OS. I am a bit concerned about my hard-ware, though and wonder if anyone out there could tell my about any susposed conflicts, etc.  My core system is listed below as part of my signature. I also have a DrayTek Vigor 2600G Wireless Router onto which my Epson Stylus Photo R300 Printer is attached. The printer is attached to my network royter so that it is treated as a print server and can be used by any computer on the network.

I will eventually be adding a SATA II disk, and it is on this new disk that Ubuntu will be installed.

How will this setup work with Ubuntu 5.10 AMD64?

I am particularly concerned about my SATA drives. I have run the Live CD version of Ubunto 5.10 AMD64 and it did not recognise my two currently installed SATA disks :( , only showing my external Maxtor One Touch disk, which is a standard IDE example.

Any help that you can provide me will be gratefully accepted.

Thank you.

---

### Post by Cuppa-Chino on 2005-11-19
[QUOTE=BadHead]
I also have a DrayTek Vigor 2600G Wireless Router onto which my Epson Stylus Photo R300 Printer is attached. The printer is attached to my network royter so that it is treated as a print server and can be used by any computer on the network.
[/QUOTE]
I was struggling with that until today but have it working now: [Printing with Vigour Router]("http://www.ubuntuforums.org/showthread.php?p=504618")
[QUOTE=BadHead]
I am particularly concerned about my SATA drives. I have run the Live CD version of Ubunto 5.10 AMD64 and it did not recognise my two currently installed SATA disks :( , only showing my external Maxtor One Touch disk, which is a standard IDE example.
[/QUOTE]
My SATA drives (on Asus P4P800 board) was found straight away, it was mounted as **_S_DA** (not HDA), so check that with the live version - best to check via System :arrow: Disks and see what LiveUbuntu recognises.
One issue you might have is that Ubuntu dumps the GRUB boot loader on HDA (IDE connected) drive, if you still have an IDE drive this should be okay. I realise some people were unhappy with this but in the end if the system looks at your old drive for the small bootloader and then goes SATA that does not cost real performance. If you want to get rid of any IDE drives, it is easy enough to install GRUB onto you SATA drive, as shown [here]("http://www.ubuntuforums.org/showpost.php?p=414321&postcount=5")
and in many other threads.

On SATA II I do not know.

---

### Post by BadHead on 2005-11-19
Thanks for taking the time to answer, Cuppa-Chino.  :)  I've noted them and when it comes to installing Ubuntu I'l' refer to them.

---

