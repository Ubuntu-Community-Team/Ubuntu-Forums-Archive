---
title: "SATA drive causes DMI Pool Data hang"
date: 2006-08-02
forum: Hardware &amp; Laptops
---

### Post by heliomedia on 2006-08-02
Hi - 

I need help on this one to try and figure out what detail I am missing.

I have a Western Digital WD2000 SATA drive which works just fine on my XP/Ubuntu double boot machine. It is formatted with NTFS. I use the onboard SATA controller and everything is fine on either operating system. The drive mounts/reads in Ubuntu, etc etc.

I want to transfer this drive to my file server which is another Ubuntu box, also Dapper and also fully updated. (see specs below)

When I boot without the SATA drive being connected (but the PCI controller is) everything is fine.

If I boot with the drive connected, I cannot get past the "Verifying DMI Pool Data" during start up. It just hangs there forever.

The motherboard BIOS was last updated a few years ago so that doesn't seem to be an option.

What can I do to get the box to boot with the SATA drive installed?

Box 1 - workstation
-------------------
Asus A7N8X-E
AMD Athlon XP 2600+
1.5Gb RAM
Windows XP SP2
Ubuntu Dapper Drake
Pioneer DVD-RW DVR-106D
Western Digital 40Gb HD WD400BB (NTFS for Applications)
Western Digital 160Gb HD WD1600JB (NTFS C drive and Root EXT3)
Initio Ultra SCSI Host adapter
Silicon Image SiI 3112 SATARaid controller (onboard) 
-------------------


Box 2 - File Server
-------------------
DFI CA64-TC socket 370 Pentium III board (new)
384 Mb RAM
LG 40x CD-R
Western Digital Caviar WD36400 6Gb ATA/33 as Ext2 root
Maxtor Diamondmax Plus 9 120Gb ATA/133 Ext3 mounted on /home
SYBA SATA3112-150R PCI SATA controller with SiI 3112 chipset
Keyspan PCI USB adapter
Realtek PCI RTL-8029 network card
-------------------

---

### Post by jared85 on 2006-08-17
did you happen to ever get this issue resolved. I have a raid sata card with the same chipset and the install goes great but then hangs after the first reboot at "verifying dmi pool data".

I read in another thread to try another install of 6.06 instead of server. Guess I will see if that works!

---

