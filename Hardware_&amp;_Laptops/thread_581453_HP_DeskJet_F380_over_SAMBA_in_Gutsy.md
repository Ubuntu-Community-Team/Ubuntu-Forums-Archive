---
title: "HP DeskJet F380 over SAMBA in Gutsy"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by Kimm on 2007-10-19
Has anyone tried this printer in Gutsy?

The printer is plugged into my fathers XP computer downstairs and shared with the network. I am able to find and install the printer, but any atempt to print a page has so far been futile.

I have found a thread that this printer should work (in Dapper): [http://ubuntuforums.org/showthread.php?t=238355](http://ubuntuforums.org/showthread.php?t=238355)

There is no exact match in the list of printers while installing, the closest is DeskJet F300. I have tried installing it using this driver and the DeskJet 3650 driver (as it has been reported working with this driver in the other thread). Both cause the printer to start making noise, but neighter produce any actuall printing.

After trying to print a test page several times (also trying to print one from my fathers computer: this worked) I noticed that my settings where set to use US Letter as paper size, while it should actually be A4. However, correcting this yielded no results.

Thoughts anyone? is it possible that the problems are actually caused by the Windows computer?

I should also note that this is a clean Gutsy install (I installed a clean Tribe 5) and it has not given me any other problems so far.

It might also be worth noting that I have had another printer connected to this computer, that strangely stoped working recently. I do however seem to remember printing some things with it after I installed Gutsy. It refuses to react to any signal I give it (I've tried pluging it in/out of both the computer and its powersource, to no avail). I'm ataching a copy of the symbol next to a yellow light (that did not use to be on before) that I am unable to identify (I have no manual). The Printer is a HP LaserJet 5L. Just in case it might be connected

---

### Post by Maulwuff on 2007-10-19
I had no probs with this printer on feisty, directly attached. The setup already had selected HP + F300 series driver and it prints well. So perhaps a share problem.

---

### Post by Kimm on 2007-10-19
I had a look at the XP computers print and print sharing settings. But I cant see anything wrong with them.

I also tried reconfiguring cups, but nothing changed :/

---

### Post by Kimm on 2007-10-20
/bump?

Doesnt anyone else have this problem? I'm sure it might be a generic printer problem, someone must have experianced something similar?

---

### Post by kazacy on 2007-10-23
same problem here but with a HP 710C. seems its a samba problem


srry its not samba.
this is from launchpad:
 [https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/131470/comments/7](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/131470/comments/7)




Do

sudo aa-complain cupsd

to deactivate the AppArmor protection of CUPS temprarily, then you should be able to print again.


worked for me
now i need to find what is AppArmor :D

---

### Post by Kimm on 2007-10-26
> **kazacy said:**
> 
Do

sudo aa-complain cupsd

to deactivate the AppArmor protection of CUPS temprarily, then you should be able to print again.


worked for me
now i need to find what is AppArmor :D

Thank you.

I tried it, but it still doesnt seem to work (Printer still makes noices, but nothing comes out) :/

---

### Post by wireless on 2007-10-26
f380 = f300 .. With hp printers the last 2 digits of the model usually refer to the printers region. 
i know for a fact sharing a printer between diffrent os types can be a pain. hp does not support it officialy either.

What i can suggest is to instal dj3650 as alternative driver on both ends. where the printer connected directly and on the remote computer (this should work becouse both drivers are LIDIL language. the same as you f380 printer.)
BTW. before you try it , first install dj3650 driver on the main pc. print test and make sure its printing properly. if this is the case go on and install it on gutsy.

good luck

---

### Post by Kimm on 2007-10-26
> **wireless said:**
> What i can suggest is to instal dj3650 as alternative driver on both ends. where the printer connected directly and on the remote computer (this should work becouse both drivers are LIDIL language. the same as you f380 printer.)
BTW. before you try it , first install dj3650 driver on the main pc. print test and make sure its printing properly. if this is the case go on and install it on gutsy.


Sounds like an idea!

I tried downloading the driver for the DJ3650 for Windows XP and installing it. But during the installation it wants me to plug the printer in for it to detect it. But since the old driver is already installed the computer detects it as an F380 and the installation program just sits there.

Is there any other way to get the drivers installed?

---

### Post by Oraclegol on 2007-10-26
i was having a similar problem how ever i was trying to use a hp 920c
what i ended having to do was
using the printing tools 
System> Printing
then clicking on New Printer
then windows printer via samba
 then browse to the printer and click ok

why problem it would add printer address as
smb://WORKGROUP/dinobreath/hpdeskje 
and it would not work to get this i just changed the host name to the ip of the machine
smb://WORKGROUP/192.168.1.101/hpdeskje

---

### Post by wireless on 2007-10-26
> **Kimm said:**
> Sounds like an idea!

I tried downloading the driver for the DJ3650 for Windows XP and installing it. But during the installation it wants me to plug the printer in for it to detect it. But since the old driver is already installed the computer detects it as an F380 and the installation program just sits there.

Is there any other way to get the drivers installed?

sorry i wasnt clear about it. you should download basic driver and install INF. [ftp://ftp.hp.com/pub/softlib/software2/COL4005/dj-13201-3/3600_enu_win2k_xpinfu.exe](ftp://ftp.hp.com/pub/softlib/software2/COL4005/dj-13201-3/3600_enu_win2k_xpinfu.exe)

you download the basic driver.. run it.. it will create a folder "3600" than go to "printers and faxes" press add printer ..usb.. have disk.. 3600.. INF.. print test.. if it prints set the dj3600 as default and share it.

---

### Post by diegomedaglia on 2007-11-16
Hi!
   Try disabling bidirectional communication for the printer in your Windows box. This was suggested in this post:[http://ubuntuforums.org/showpost.php?p=2646556&postcount=3]("http://ubuntuforums.org/showpost.php?p=2646556&postcount=3")
It woked OK for me! I'm using printing to a shared HP Deskjet 3470 connected via USB to a Windos 98 computer.

Hope that helps!

---

### Post by rodrigo666 on 2008-04-11
I'm having the same problem, any of the tips here solved your problem?

---

### Post by rodrigo666 on 2008-04-11
> **diegomedaglia said:**
> Hi!
   Try disabling bidirectional communication for the printer in your Windows box. This was suggested in this post:[http://ubuntuforums.org/showpost.php?p=2646556&postcount=3]("http://ubuntuforums.org/showpost.php?p=2646556&postcount=3")
It woked OK for me! I'm using printing to a shared HP Deskjet 3470 connected via USB to a Windos 98 computer.

Hope that helps!

It worked like a charm! Thanks!

---

