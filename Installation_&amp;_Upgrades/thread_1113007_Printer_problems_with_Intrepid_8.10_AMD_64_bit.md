---
title: "Printer problems with Intrepid 8.10 AMD 64 bit"
date: 2009-04-01
forum: Installation &amp; Upgrades
---

### Post by kevingtonbeare on 2009-04-01
I have just installed Ubuntu 8.10 having been using 8.04 LTS.  Computer is a 64 bit AMD with 1 GB main memory.  Main reason for the upgrade was to overcome printing problems with Qcad Professional.

Background: In 8.04 Administration->Printing showed two printers, Deskjet 9300 and PDF.  (My actual printer is an HP Deskjet 1180C.) When printing drawings from Qcad, the Qcad print dialog allowed only printing to PDF and did not even show the physical printer.

Current situation:  I did a clean install of 8.10 (reformatting the disk partitions).  The system found the deskjet 1180c, which it correctly named in the dialog box, however, the driver the system found for this printer is for the dj 1125C.  When printing a test page or a drawing, the output is reduced by 50% across the page and 10.5% down the page.  Thus circles come out as ellipses.

If I print to a PDF file, and move the .pdf file to the Windows file system and print it from Windows, I get perfect output. Has anyone else encountered a similar problem and found a solution?

Thanks, kevingtonbeare.

---

### Post by kevingtonbeare on 2009-04-05
Problem appears to be no entry for the deskjet 1180c in models.dat

I did this:
downloaded the latest hplip package

cd to /usr/share/hplip/data/models

sudo chown your_usrname_your_usrname models.dat

edit models.dat with Gedit

As the driver for the 9300 works for the 1180c, find the block describing the 9300, copy it to the clipboard and paste just under the original 9300 block.  Now rename the duplicate block to 1180c

Save the file, ignoring the warning about not being able to create a backup of the original models.dat

sudo chown root:root models.dat

cd   (to go to your home directory)

hp-setup

This will create an 1180c printer, however, the system may have an original, broken, entry for this printer.  Delete the first entry and make the new one your default.

Worked for me.

However, why the retrograde step from LTS 8.04?????

Cheers

---

