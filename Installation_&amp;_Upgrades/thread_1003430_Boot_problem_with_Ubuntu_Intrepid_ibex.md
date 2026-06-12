---
title: "Boot problem with Ubuntu Intrepid ibex"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by Jemup on 2008-12-06
Hi everyone,
I'm writing in this forum because I'm seeking help about a problem I've encountered while booting my machine with Ubuntu 8.10 Intrepid Ibex. I installed Ubuntu using a formatted hard disk, in the mean time I've two other hdisks: one dedicated for Windows, the other utilised as a Storage. Now when the machine starts to boot the OS I'm able to choose which OS i want to boot, in this case Ubuntu or Win. When i choose Ubuntu the pc freezes before getting to te login page showing me a sort of error which seems to loop every "n" seconds (20-30secs), after 4-5 minutes of this the boot process continues normally granting me the login page. The error that loops:

[B][35.0077550] ata7.00: expection mask 0x0 Emask 0x0 SAct 0x0 Serr 0x0 action 0x6 frozen
[35.0077600] ata7.00: cdm c8/00:01:00:5f:64/00:00:00:00:00/e2 tag 0 dma 512 in
[35.0077601]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout) 
[numbers] ata7.00:status: { DRDY } [/B]

In first place I would like to know what those entries mean, because while researching with google about that error I found that in most of cases there are errors in the hd, but i don't think that is my case.

I can access Ubuntu without the error if I access the GRUB hidden menu adding "all_generic_ide" at the end of the Kernel boot option. The problem is that if I modify permanently the file "menu.lst" in Ubuntu adding that entry, the error shows up regardless (I verified that accessing the GRUB hidden menu after the modification of "menu.lst" the entries "all_generic_ide" is present!). The error doesn't show up if i reboot my Pc from the Ubuntu environment.

Best regards, 
Alessandro

---

### Post by Jemup on 2008-12-06
I've just noticed the error in **/var/log/dmesg** :I've found these entries repeated a fex times in the log:

[    6.273986] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000e79cd00001d7d]
[   35.077550] ata7.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   35.077600] ata7.00: cmd c8/00:01:00:5f:64/00:00:00:00:00/e2 tag 0 dma 512 in
[   35.077601]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[   35.077691] ata7.00: status: { DRDY }
[   40.117524] ata7: link is slow to respond, please be patient (ready=0)
[   45.101525] ata7: device not ready (errno=-16), forcing hardreset
[   45.101534] ata7: soft resetting link
[   45.290289] ata7.00: configured for UDMA/100
[   45.304587] ata7.01: configured for UDMA/66
[   45.304594] ata7: EH complete

As i can read, **"link is slow to respond"**. Unfortunately I have no idea how to solve this kind of problem. I hope someone will help me in this :)

---

