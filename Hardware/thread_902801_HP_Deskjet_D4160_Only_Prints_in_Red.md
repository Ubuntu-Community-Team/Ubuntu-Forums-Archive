---
title: "HP Deskjet D4160 Only Prints in Red"
date: 2008-08-27
forum: Hardware
---

### Post by End3r on 2008-08-27
I recently got an HP Deskjet D4160 and I have connected it to my Dell M1330 via USB.  The printer prints fine, however everything it prints is in the same color of dull red.  (Think brick color.)

The printer works fine when I print using Vista.  Everything printed in Ubuntu (including the test pages etc.) prints in red.

hp-toolbox reports that the ink cartridges are both fine (one color and one black.)

Any help would be greatly appreciated.

---

### Post by phidia on 2008-08-27
Do you have the hplip package installed? Try that and be sure you are using the correct driver for your printer too.

Edit:Ok my bad you must have the hplip package if you have the toolbox. I would check to see you are using the correct driver.

---

### Post by End3r on 2008-08-27
how/where would I check the drivers (yes, I do have hplip installed)

---

### Post by phidia on 2008-08-27
Are you using 8.04? System > Admin > Printing should give you more details.

There are more details about your printer at the opening printing database [here]("http://openprinting.org/show_printer.cgi?recnum=HP-Deskjet_D4160"). Oddly for an HP it does show it working partially.
Even though [this]("https://help.ubuntu.com/community/HPPrinterInstallation") wiki is for previous releases you might find some help there too.

---

### Post by End3r on 2008-08-27
The only info I could find there that appeared to be related to a driver was```
Make and Model: HP DeskJet D4100 Foomatic/hpijs, hpijs 2.8.2
```

Is this what I'm looking for?

EDIT: I tried updating hplip to 2.8.7 and this did not resolve the problem; still red test pages

---

### Post by phidia on 2008-08-27
Try printing from the commandline using "lp" perhaps there will be output that will help troubleshoot this?

---

### Post by End3r on 2008-08-27
sadly the only output is the job id "request id is HPDeskjetD4160-28 (1 file(s))
" for example.

The pages all print sucessfully, but in shades of the same red color.

---

### Post by phidia on 2008-08-27
This is a tough one. If it were me I would delete the printer you installed and re-install it. 
I'm guessing text only pages print red too?

Hang in there someone may have an answer-we'll figure it out by trial an error.

---

### Post by End3r on 2008-08-29
I have deleted the printer several times, sadly to no avail.

Text, Images or indeed anything that comes out of the printer is in red.

---

### Post by gjoellee on 2008-08-29
> **End3r said:**
> The only info I could find there that appeared to be related to a driver was```
Make and Model: HP DeskJet D4100 Foomatic/hpijs, hpijs 2.8.2
```Is this what I'm looking for?

EDIT: I tried updating hplip to 2.8.7 and this did not resolve the problem; still red test pages

have you checked the ink manually? The printer may give bad readings to your computer:confused:

---

### Post by End3r on 2008-08-29
No, I haven't but the printer works fine with vista leading me to believe that this is a software/configuration issue not hardware.

---

### Post by phidia on 2008-08-29
> **End3r said:**
> No, I haven't but the printer works fine with vista leading me to believe that this is a software/configuration issue not hardware.

I believe you. It would be helpful, I think, to run a livecd (knoppix, zenwalk-live, an older version of ubuntu?) and set up the printer in that environment and see if it works normally.

Other than directing you to the [openprinting.org forums]("http://forums.openprinting.org/index.php?18") I don't know what other resolution there is. I think you probably found a bug-you could report it at [launchpad]("https://launchpad.net/ubuntu").

---

### Post by End3r on 2008-08-29
I will download a live cd and test and then post my findings.

In the meantime I have set my printer to print in gray scale (via Administration>Printing>Printer Options.)  This does allow me to print pages in black ink.

EDIT: Bug posted [https://bugs.launchpad.net/ubuntu/+bug/262841](https://bugs.launchpad.net/ubuntu/+bug/262841)

---

### Post by Mularkey23 on 2008-09-01
I had the same problem.  Go to print settings>properties>settings>device>print out mode and choose greyscale.  That should fix it.  Cheers

Edit:  Skipped over that last post sorry

---

