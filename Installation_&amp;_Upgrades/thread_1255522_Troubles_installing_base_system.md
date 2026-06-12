---
title: "Troubles installing base system"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by pannemanm on 2009-09-01
Hi,
 
I'm trying to reinstall my ubuntu server from scratch. Everything goes right until the cd starts installing the base system. I'm getting the next errors:
 
Install Base system Debootstrap warning
Warning: 
- [file:///cdrom/pool/main/x/xfonts-terminus/console-terminus_4.26-2.1_a11.deb](file:///cdrom/pool/main/x/xfonts-terminus/console-terminus_4.26-2.1_a11.deb) was corrupt
- Could not download package console-terminus
- [file:///cdrom/pool/main/x/xapian-core/libxapian15_1.-.7-4_i386.deb](file:///cdrom/pool/main/x/xapian-core/libxapian15_1.-.7-4_i386.deb) was corrupt
- Could not download package licxapian15
- Failure while configuring base packages. This will be attempted 5 times
Unable to install busybox-initframes. An error was returened while trying to install the busybox-initframes package onto the target system. Check /var/log/syslog or see virtual console 4 for the details
 
After continueing everything, The installer returns to the main installation menu. 
In the syslog I see lines containing errors "Configuring bootstrap-base failed with error 1
 
I've reburned the image on several new disks, als on low speeds. I've also downloaded the image again and burned this image, but I keep getting the errors.
 
I've ran checkdisk from the boot loader of the comp, but that gave me no errors.
 
On the cdrom integrity check, I get errors that the following files have failed the md5 checksum verification:
- linux-restricted-modules-2.6.28-11-server_2.6.28-11.15_i386.deb
 
System I'm reinstalling on is a Dell Optiplex GX260 SFF, with 2 GB RAM and 140 GB harddisk

---

### Post by pannemanm on 2009-09-01
I also tried an integrity check on one of my laptops (dell lat d630). this check was performed without any errors. I'm getting the impression the problem isn't in the disk, but in the player. I'll try to clean the head first an then try to perform an installation again.

---

### Post by Jose Catre-Vandis on 2009-09-01
How old / what sort of state is your CD rom drive in?

I would get similar errors on installation until I swapped out the CD rom drive for a different (and obviously better) one. Admittedly the original was probably last century vintage, or at least just post millenium :)

---

### Post by pannemanm on 2009-09-01
The drive that's currently in the system is from 2005. I've already cleaned it, but it generates only more errors than I had before.

---

### Post by pannemanm on 2009-09-01
I suspect there is a different hw problem than only the cdrom drive. Maybe related to the IDE connector on the mobo.
I was planning on buying a new, lowbudget system for &#8364; 300,- with an Intel Atom 330 processor, 2 GB of RAM, 320 GB Harddrive, Lan 10/100/1000, wlan 802.11 b/g/n. Chassis is SFF, about the same measurements as the GX260 which is currently me (defective) ubuntu server.
System will be delivered with Vista by default, but that's gone as soon as the comp is ready for use.

---

### Post by Jose Catre-Vandis on 2009-09-01
How about USB installation?

---

### Post by pannemanm on 2009-09-02
Don't have an USB stick large enough, but it is supported bij de optiplex.

---

### Post by pannemanm on 2009-09-02
Alright, server is up and running again on a new machine. It seemed to be a hardware problem

---

