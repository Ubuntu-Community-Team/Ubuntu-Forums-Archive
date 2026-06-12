---
title: "Cannot boot after Server installation"
date: 2009-09-21
forum: Installation &amp; Upgrades
---

### Post by superchivo on 2009-09-21
Hi!  please bear with me on this one for it is a little complicated (for me at least ... :(  )

I installed Smoothwall Express 3.0 on a HP ML150 G5 server, but after running into nasty problems, I decided to go with Ubuntu Server 9.04  The installation process went perfect, with no errors, all hardware was detected, my primary HD (SCSI 0,1,0) sda, was partitioned perfectly (in theory), and everything worked just dandy.

However, when booting the server again, it does so from Smoothwall instead of Ubuntu, and the boot loader does not even "see" the Ubuntu installation. I've tried to re-install, Repair, and re-install the grub onto "hd0" without result.  It always boots an incomplete installation of SWE 3, and freezes the system.

What can I do to "force" the system to boot from my newly installed Ubuntu server ?

I will greatly appreciate any help.

---

### Post by BraedenNaylor on 2009-09-21
I had this problem and could not get GRUB to install properly. In the end I had to restore the drive from a backup, including bootloader, then format, format again with partion editor from live CD. Took me a day to figure out without support. I'm hoping there is an easier solution for you. If not start backing any needed data up.

-Braeden

---

