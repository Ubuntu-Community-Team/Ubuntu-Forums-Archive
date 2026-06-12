---
title: "HP 1510 printer, how to monitor ink levels?"
date: 2007-02-22
forum: Hardware &amp; Laptops
---

### Post by StanMeis on 2007-02-22
I bought and successfully installed an HP1510 all in one printer, scanner, copier in Ubuntu 6.06 over the holidays on my wife's computer.  Recently she ordered a book in PDF form and printed over 100 pages and said that the black print started streaking on the last few pages she printed.  We bought a new black cartridge and I suspect that is the problem but the empty cartridge light is not flashing yet so I wanted to try cleaning the print heads and check the ink levels so I could get the maximum use from the cartridge before replacing it.  I looked at the manual thinking I could possibly do clean the heads by holding a button down but found that cleaning the ink jets and checking levels is done via a software utility.  The manual only explains how to do this in Windows and Mac using the bundled software so I tried to locate the Linux version of the utility on her system to accomplish the task but was unable to find anything.  It's been a couple months since I installed it so I could be forgetting where it would be located.

Does anyone else have experience with a similar HP printer?  Are Linux users "flying blind" for some of the printer's functions such as checking ink levels and cleaning print heads or is there a way to do it in Ubuntu?  I followed all the instructions available when installing the printer and didn't see anything about checking ink levels or cleaning the print heads.  Either I'm not finding something or it's not included in HP's Linux drivers but I thought the Linux printer website said that this printer had full functionality in Linux.  To me "full functionality" would include being able to check ink levels and clean the print heads.

Anyone have any suggestions?  I'm sure that replacing the cartridge will solve the streaking problem but I'd like to figure out how to check ink and clean the heads for future reference.

---

### Post by tgalati4 on 2007-02-22
HP printers are better supported than most under Linux.  Some functions are better handled at the printer's front panel.  Usually hit the option or setup button repeatedly until you get to the maintenance pick, then hit enter.  Scroll until you get to clean print head.

Also check the hp website.  Sometimes there are linux-based control panels for their more popular printers.

In firefox try:

localhost:/631

See what functions are available for your printer.

I have an old Laserjet 4 printer that I have set for "Stop on low toner".  It will automatically send a message to CUPS that the printer is stopped due to low toner.  There may be a similar setting on the inkjet so it will stop on low ink.  CUPS will always report status for a stopped printer.

Good luck

---

### Post by ramjet_1953 on 2007-02-22
Do you have [COLOR="Red"]hplip[/COLOR] installed?

If not, you can install it using Synaptic.

It lets you monitor even more things than Redmond's equivalent.

Regards,
Roger :cool:

---

### Post by jake3988 on 2007-03-09
I have a hp too and have hplip installed... but how do I get that device manager?  Or, alternatively, where's it located/called?

---

### Post by ramjet_1953 on 2007-03-10
hp-toolbox shold be installed as part of HPLIP.

Go to : System>Administration>HPLIP Toolbox

If for some unknown reason there isn't an item for it in System>Admintration, just type in a console hp-toolbox and it should open.

Regards,
Roger :cool:

---

