---
title: "How do I get SATA to hotswap / automount?"
date: 2013-03-28
forum: Hardware
---

### Post by webdesigncompanyla on 2013-03-28
I'm trying to do the same thing with a KF-1000-BK 3.5" hotswap rack by Kingwin (kingwin.com).

I can't get it to work so far.

Here are the issues that I think you all have outlined:

1) AHCI (on or off in bios)
2) chipset needs to support hotswap (how do I determine this? I have a M2N6B-LA motherboard in an HP computer.)
3) some kind of script can do it (I dont want to use a script, it should just work.)

Any help would be appreciated in getting this hotswap tray to work so I can easily make backups/restores.

edit: I'm running Ubuntu 12.04 LTS.

From the motherboard manufacturer web site:

"SATA on the Go
This  motherboard supports the next-generation hard drives based on the  Serial ATA (SATA) 3Gb/s storage specification, delivering enhanced  scalability and doubling the bus bandwidth for high-speed data retrieval  and saves. The external SATA port located at the back I/O provides  smart setup and hot-plug functions. Easily backup photos, videos and  other entertainment contents on external devices."

http:// usa.asus.com/Motherboards/AMD_AM2Plus/M2N68VM/

And... the system is setup for a HP Personal Media Drive.  This tells me it can do hotswap, but I would like to use the Kingwin tray since the HP Personal Media Drives are either too small and/or too expensive.

Any help is appreciated.

---

### Post by webdesigncompanyla on 2013-03-28
figured it out after 2 years of not being able to do it...

my hotswap is plugged into the sata3 port on my motherboard (it says SATA3)

so i type this in terminal to rescan if i plug in or remove a drive after booting up:


echo "- - -" | sudo tee -a /sys/class/scsi_host/host3/scan



apparently you need to spin down the drive first (which i didnt do the first few times testing this out by typing:

sudo hdparm -Y /dev/sdb
got it from here:
[http://forums.bodhilinux.com/index.php?/topic/6541-solved-hot-swapping-sata-drives/](http://forums.bodhilinux.com/index.php?/topic/6541-solved-hot-swapping-sata-drives/)

---

### Post by webdesigncompanyla on 2013-04-04
update: the above is only working for me if i boot with a hard drive in my hotswap bay, otherwise it's not detecting it no matter what i try

---

### Post by Elfy on 2013-04-04
moved to it's own thread - better to not bump a 2 year old thread and hope people bother to look at it

---

