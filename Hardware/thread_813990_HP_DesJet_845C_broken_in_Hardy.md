---
title: "HP DesJet 845C broken in Hardy"
date: 2008-05-31
forum: Hardware
---

### Post by plainwhitetoast on 2008-05-31
I have an HP DeskJet 845C printer.
It worked very well in Gutsy Gibbon (7.10), and still works if I boot from Gutsy Gibbon DVD.
Some time ago I upgraded to Hardy Heron (8.04) and it doesn't work anymore, if I try to print, it just prints strange symbols.

It tried to uninstall (purge) all cups and lpr related packages, reboot, and reinstall them, but the situation is the same.

What can I do?

---

### Post by Rising_Sun on 2008-07-01
I am facing the same trouble with HP Deskjet 845C in UBUNTU 8.04 and more unfortunately its my first experience on any Linux OS and getting really difficult to seek help on various such issues specially this printer issue and my scanner Mustek Bearpaw 1200 (not working in Ubuntu)

Anybody please help!!:(

---

### Post by Rising_Sun on 2008-07-02
Dear White Toast!!

I removed the printer and reinstalled, yet the problem was not resolved But there was another thing wrong....that I incidentally Found. In System---------> Administration--------> Printing

1- First was the Printer Description Written as "HEWLETT-PACKARD
DESKJET 845C"

The Next Dialogue was location which I suppose was
empty because it might have been for network printers,

Then third Option Was Device Url:
"hp:/usb/DeskJet_845C?serial=TH187179S9SX" This was all OK BUT

Next thing I found there was PRINTER MODEL Written as HP-Deskjet
845-C FOOMATIC. This "foomatic" thing placed me in doubt and

2- When I went to System-------->Preferences----->Hplip Toolbox....
there is a Tab "Tools" and third option in that Tab is "VIEW DEVICE
INFORMATION" Its a long list of Device Stats and problems even it
tells you the ink status and health of cartridge if you can read
and understand carefully.

In this option I found out My Printer Model was Written as HP-DESKJET-845c- CUPS and Model Detail was HP 845-cvr

So My Printer was not Foomatic Kind it was a CUPS Kind.

Therefore I then Go Back to In System---------> Administration--------> Printing and in SETTINGS TAB I Changed the Third Option i.e. HP DeskJet 845-C Foomatic to HP DeskJet 845C - CUPS+Gutenprint v5.0.2

Then I Set My Printer as Default here and Go back to Hplip and Set The Current Printer as Default Again, and Run the "Allign Cartridges" Option Under Tools Tab (Which you can say was Printer Calibration your Printer's Case)

I Printed the Test Page and Its Working Fine Now.

Now I have posted all the above detail so someone else may also get Help from here and perhaps some next time you will also be able to help someone in more detail

Long Live Ubuntu Forums:guitar:

---

