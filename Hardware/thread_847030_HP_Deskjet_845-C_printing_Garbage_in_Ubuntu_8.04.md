---
title: "HP Deskjet 845-C printing Garbage in Ubuntu 8.04"
date: 2008-07-02
forum: Hardware
---

### Post by Rising_Sun on 2008-07-02
I am facing the trouble of Garbage Priniting with HP Deskjet 845C in UBUNTU 8.04 and more unfortunately its my first experience on any Linux OS and getting really difficult to seek help on various such issues specially this printer issue not working in Ubuntu)

I Don't Even know if its the right place to post this thread or not so please excuse me if I reached the wrong place yet help me out and I Shall be glad

Anybody please help!!:confused:

---

### Post by starcannon on 2008-07-02
I'm no printer guru, I only run HP they just work, and I always install the rest of the HPLIP packages from 
System-->Administration--Synaptic Package Manager

Then I go to:
System-->Administration--Printing
and install my printer:
New-->follow the wizard.

I don't know your printer, but perhaps it needs recalibrated, on mine I print out a page (printer has a button for it) and run that through the scanner, and its callibrated. Not sure if theres a callibration tool in HPLIP Toolbox or not, but its worth a look System-->Preferences-->HPLIP

Anyway thats about all I can say for it, I've never had to do anything special to make my HP printers work in Linux.

---

### Post by Rising_Sun on 2008-07-02
Dear Starcannon! I really appreciate the help extended by you and am thankful for the time you have taken out! 

Although I already did the Steps you told but still I removed the printer and reinstalled on the lines you guided me through, yet the problem was not resolved But there was another thing wrong....that I incidentally Found. In System---------> Administration--------> Printing

1- First was the Printer Description Written as "HEWLETT-PACKARD     
   DESKJET 845C" 
   
   The Next Dialogue was location which I suppose was  
   empty because it might have been for network printers, 
   
    Then third Option Was Device Url:
   "hp:/usb/DeskJet_845C?serial=TH187179S9SX" This was all OK BUT

   [COLOR="Red"] Next thing I found there was PRINTER MODEL Written as HP-Deskjet   
    845-C FOOMATIC. This "foomatic" thing placed me in doubt and [/COLOR]

2-  When I went to System-------->Preferences----->Hplip Toolbox....
   there is a Tab "Tools" and third option in that Tab is "VIEW DEVICE 
   INFORMATION" Its a long list of Device Stats and problems even it 
   tells you the ink status and health of cartridge if you can read  
   and understand carefully.

In this option I found out My Printer Model was Written as HP-DESKJET-845c- CUPS and Model Detail was HP 845-cvr

So My Printer was not Foomatic Kind it was a CUPS Kind.

_Therefore I then Go Back to In System---------> Administration--------> Printing and in SETTINGS TAB I Changed the Third Option i.e. HP DeskJet 845-C Foomatic to HP DeskJet 845C - CUPS+Gutenprint v5.0.2_

Then I Set My Printer as Default here and Go back to Hplip and Set The Current Printer as Default Again, and Run the "Allign Cartridges" Option Under Tools Tab (Which you can say was Printer Calibration your Printer's Case)

I Printed the Test Page and Its Working Fine Now.

Once Again I Thank You very much for your help, as It was my first ever experience on Ubuntu Forums and I am really encouraged that people really care to help here.

Now I have posted all the above detail so someone else may also get Help from here and perhaps some next time you will also be able to help someone in more detail :)

Long Live Ubuntu Forums :guitar:

---

### Post by starcannon on 2008-07-02
Excellent, mark as solved and put some good tags on it to make it an easier solution for others to find.

Nice work!

---

