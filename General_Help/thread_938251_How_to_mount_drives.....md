---
title: "How to mount drives....?"
date: 2008-10-04
forum: General Help
---

### Post by seymour71 on 2008-10-04
I can't seem to get Ubuntu to find my SATA hard drives.

This is the output from fdisk:

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x36f936f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2327    18691596   83  Linux
/dev/sda2            2328        2434      859477+   5  Extended
/dev/sda5            2328        2434      859446   82  Linux swap / Solaris


I currently have 1 drive one IDE that I've installed Ubuntu on, and two SATA drives, one with vista on. How can I get these recognised? 

I am quite new to Ubuntu, so please be gentle with me!

---

### Post by seymour71 on 2008-10-09
Sorted It!

I updated the BIOS, and that enabled me to set the RAID to ATCH (or something like that) I rebooted and Ubuntu sees them now!:)

---

### Post by fjgaude on 2008-10-09
Hapyy you solved your own problem...

---

### Post by seymour71 on 2008-10-09
:(

Seems I spoke too soon. If I leave the RAID settings on ATCH(?) Windows can't see the sata drives!

---

### Post by fjgaude on 2008-10-09
Maybe in your BIOS if you pointed to the drive that Vista is on it might boot and work correctly.

---

### Post by seymour71 on 2008-10-10
Hi mate, I'm not sure I understand. BIOS can see the discs, but Ubuntu can't.

---

### Post by hyper_ch on 2008-10-10
You can integrate sata drivers into windows by slipsteraming it. I think if youw ill slipstream SP3 into your winxp then it will have them included. If not, check the homepage of your mainboard's producer to download the sata drivers.

Use nLite to slipstream: [http://en.wikipedia.org/wiki/NLite](http://en.wikipedia.org/wiki/NLite)

---

### Post by seymour71 on 2008-10-10
Man I'm getting really confused now! Windows does recognise the drives, but only if i set the BIOS to IDE RAID. If I set the BIOS to ATCH RAID, Windows can't see them, but Ubuntu can.

My drivers & BIOS are all up to date, as the Mobo has a utility to do it automatically. Do you think I still need to do this Nlite thingy? never heard of it before.

---

### Post by hyper_ch on 2008-10-10
windows xp incl. sp2 does not have by default SATA drivers integrated hence you need to switch to legacy (ide) mode for windows to recognize it... however you can patch/slipsteram win xp install cd with sata drivers...

---

### Post by seymour71 on 2008-10-10
Ahhhhh...! Think I understand; If i do the slipstream thingy, I can leave the BIOS on ATCH mode and then XP and Ubuntu will both see the drives?

---

### Post by hyper_ch on 2008-10-10
yes :) I'm not sure if SP3 will suffice... best to check your mainboards manufacturer if they also provide SATA drivers that you can slipstream...

---

### Post by seymour71 on 2008-10-10
Nice one mate, I'll give it a go tonight.

---

