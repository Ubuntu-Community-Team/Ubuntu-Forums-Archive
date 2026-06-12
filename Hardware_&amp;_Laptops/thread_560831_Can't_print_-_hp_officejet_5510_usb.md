---
title: "Can't print - hp officejet 5510 usb"
date: 2007-09-26
forum: Hardware &amp; Laptops
---

### Post by MeNoKnow on 2007-09-26
Help I'm pulling my hair out! Another stuck newbie.  Everything looks ok but all print jobs stop with no output.  My system: omnibook 900b 192K p3 450 4 port usb hub,unbuntu 7.04, hp officejet 5510


POSSIBLY IMPORTANT: sprint pantech px 500 pcmcia wireless internet, needing usb serial driver modification (replace stock with vendor,model for pantech card) !?

from GUI Administrstion -> Printing:

   hp:/usb/officejet_5500_series?serial=MY49TG096

FROM THE TERMINAL:

 /usr/lib/cups/backend/hp

direct hp:/usb/officejet_5500_series?serial=MY49TG20Z096 "HP officejet 5500 series" "HP officejet 5500 series USB MY49TG20Z096 HPLIP" "MFG:HP;MDL:officejet 5500 series;CLS:PRINTER;DES:officejet 5500 series;SN:MY49TG20Z096;"

Some messages:

cups admin error log:

E [23/Sep/2007:17:12:11 -0400] Creating missing directory "/var/run/cups/certs"
E [23/Sep/2007:17:22:42 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [23/Sep/2007:17:23:26 -0400] cupsdAuthorize: Local authentication certificate not found!
E [23/Sep/2007:17:23:26 -0400] cupsdAuthorize: Local authentication certificate not found!
E [23/Sep/2007:17:23:26 -0400] cupsdAuthorize: Local authentication certificate not found!
E [23/Sep/2007:17:23:28 -0400] cupsdAuthorize: Local authentication certificate not found!
E [23/Sep/2007:17:23:28 -0400] cupsdAuthorize: Local authentication certificate not found!
E [23/Sep/2007:17:23:28 -0400] cupsdAuthorize: Local authentication certificate not found!
E [23/Sep/2007:17:23:31 -0400] cupsdAuthorize: Local authentication certificate not found!
E [23/Sep/2007:17:23:42 -0400] cupsdAuthorize: Local authentication certificate not found!
E [23/Sep/2007:17:23:42 -0400] CUPS-Delete-Printer: Unauthorized
E [23/Sep/2007:17:26:33 -0400] PID 6160 (/usr/lib/cups/daemon/cups-driverd) crashed on signal 9!
E [23/Sep/2007:17:27:06 -0400] [Job 20] No %%BoundingBox: comment in header!
E [23/Sep/2007:17:27:19 -0400] PID 6273 (/usr/lib/cups/filter/pstoraster) crashed on signal 11!
E [23/Sep/2007:17:57:16 -0400] Creating missing directory "/var/run/cups/certs"
E [23/Sep/2007:17:59:55 -0400] [Job 21] No %%BoundingBox: comment in header!
E [23/Sep/2007:18:00:04 -0400] PID 5405 (/usr/lib/cups/filter/pstoraster) crashed on signal 11!
E [23/Sep/2007:18:12:01 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [23/Sep/2007:18:14:03 -0400] cupsdAuthorize: Local authentication certificate not found!
E [23/Sep/2007:18:14:03 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [23/Sep/2007:18:41:46 -0400] PID 8533 (/usr/lib/cups/filter/pstoraster) crashed on signal 11!
E [23/Sep/2007:18:42:36 -0400] [CGI] Unable to scan "@LOCAL"!


HP Linux Imaging and Printing System (ver. 1.7.3)
HP Device Manager ver. 9.0:

X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

Any ideas where to look?  What to do?  Thanks in advance.

---

### Post by dawonn on 2008-05-11
Take a peek:

[http://ubuntuforums.org/showthread.php?p=2521809#post2521809](http://ubuntuforums.org/showthread.php?p=2521809#post2521809)

---

### Post by user1234 on 2008-05-17
> **dawonn said:**
> Take a peek:

[http://ubuntuforums.org/showthread.php?p=2521809#post2521809](http://ubuntuforums.org/showthread.php?p=2521809#post2521809)

I'm sorry, where did he mention XP?  I have the same problem, usb direct to Ubuntu computer, no XP involved... do you mean to say Ubuntu needs someone to have XP installed to print?

---

