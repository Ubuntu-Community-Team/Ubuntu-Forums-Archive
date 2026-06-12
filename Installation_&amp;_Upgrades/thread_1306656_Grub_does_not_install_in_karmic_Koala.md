---
title: "Grub does not install in karmic Koala"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by slayer^_^ on 2009-10-30
Today I put my two sata drives in raid (bios raid) and tried to do a clean install of karmic after a manual partitioning... 
Everything goes fine, the raid disks are both recognized and installation goes forward smoothly but it suddenly stops when trying to install grub at the end of the installation.

With the graphic Installer (live cd) it tells me that grub hasn't been installed and the system won't boot, with the alternate grub just doesn't install... I didn't try with lilo because I just don't want to use Lilo...

I tried both amd64 and x86 32 bit version of ubuntu but... nothing.

I thought it was because of a trouble writing into the RAID disks MBR, but I did an installation of amd64 version of Jaunty (alternate version, though I didn't try the live cd one) and everything went fine (Grub installed). Then I did an upgrade and, after a few very unrelevant applet-crashes i believe that my karmic is ok!

So, I would really like to do a fresh install of karmic (I don't like upgraded systems), what should I do?
Using Lilo and the Intrepid-like terminal grub setup is not an option...

Thank you

---

