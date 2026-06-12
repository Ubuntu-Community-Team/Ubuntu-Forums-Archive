---
title: "z25 printer"
date: 2010-07-11
forum: Hardware
---

### Post by Will130278 on 2010-07-11
Hello

I'm a new user of ubuntu and a new user to this forum

With regard to the compatibility of the lexmark z25 printer, does anyone have a solution that defintely works, and is easy enough for a non linux user to understand?

I've seen various "solutions" on the internet, but I haven't yet found one that works!

---

### Post by pdc on 2010-07-12
this page

[http://www.openprinting.org/printers/manufacturer/Lexmark](http://www.openprinting.org/printers/manufacturer/Lexmark)

lists known information about printers (lexmark) and linux

I don't see the z25 listed; the z23 is described as a paperweight

lexmark was not good with inkjet printers; I think they are doing linux drivers now, but older printers may not be supported;

HP or Epson or Brother (and Canon) are supported;

folks cite HP as the best supported; the others offer drivers from their websites, so check the websites first

---

### Post by Will130278 on 2010-07-15
Right.. I've managed to get limited functionality... I can print, not always correctly, I can't align the heads and view cartridge levels, but never mind, at least I can print.

I followed advice to extract the files from the red hat versions of the drivers, converted the rpm files to deb files and installed them.

the 4 packages i installed were the z35 driver from the lexmark site, the z35 printer development kit, the z35 cups driver from a third party download site and the c++5 libraries.

This seems to get the printer just about doing what it ought to.

---

### Post by Will130278 on 2010-07-15
Ok, I've tried to retrace my steps...

I think this guide below describes what I did. If anyone tries it and it works for them as well, let me know:-



1. Make a directory within your Downloads directory and name it lextemp.
2. Download and install the  libstdc++5_3.3.6-17ubuntu1_i386.deb  package from here [http://packages.ubuntu.com/jaunty/i386/libstdc++5/download](http://packages.ubuntu.com/jaunty/i386/libstdc++5/download)
3. Download  CJLZ35LE-CUPS-2.0-1.TAR.GZ from [http://www.downloaddelivery.com/srfilecache/CJLZ35LE-CUPS-2.0-1.TAR.GZ](http://www.downloaddelivery.com/srfilecache/CJLZ35LE-CUPS-2.0-1.TAR.GZ)  and place in the lextemp directory.
4. Right click and extract to the same directory. This will produce an unzipped .tar file.
5. Delete the original .tar.gz file.
6. Right click the .tar file and extract this to the same directory. Delete the original  .tar file
7. Go into the newly created folder and delete the license and readme files. Cut and paste the gz.sh file into the lextemp dir, then delete the new directory. This gz.sh type file is incompatible with Ubuntu.
8. Open a terminal, type sudo -i then enter your password.
9. Type cd .. cd home cd (your name) cd Downloads then cd lextemp. Type ls to see the files.
10. Type tail -n +143 lexmarkz35-CUPS-2.0-1.gz.sh > install.tar.gz to convert the incompatible file into a tar.gz file named install.
11. Type ls to check, type rm  lexmarkz35-CUPS-2.0-1.gz.sh  to delete the gz.sh file, enter exit twice to exit the terminal, then return to the lextemp window.
12. Right click and extract the install.tar.gz file, then delete it.
13. Rename the Install directory Install1
14. Go into the new folder then cut and paste everything to the lextemp directory. Delete the install1 folder.
15. Repeat steps 8 and 9.
16. We now need to convert the unsuitable .rpm files to .deb files. To do this enter alien -k --scripts z600cups-1.0-1.i386.rpm . Ignore the error message.
Now repeat this operation with the file  z600llpddk-2.0-1.i386.rpm . Now type ldconfig and press enter.
17. Enter exit twice, return to the lextemp window, then install both .deb files by double clicking them.
18. Make a folder in lextemp called otherdriver .
19. Download CJZ35LE-1.0-1.tar.gz from the Lexmark website and place it in the otherdriver directory.
20. Now repeat steps 4 - 16 with this file, treating the otherdriver directory as the lextemp one was previously. This time only one .rpm file will be generated.
21. Double click the new .deb file in the otherdriver directory to intstall the package.
22. Close everything and restart the computer.
23. Try installing the printer as normal. The printing application should now show a Z35 option in the list. Select it. There should be 2 drivers shown. Try them both, one should work and enable you to print a test page.

---

### Post by Will130278 on 2010-07-15
Correction...

in step 16 and onwards, replace "z600" in the name of the file with  "z35" or whatever the file is called, type in ls to check.

---

### Post by pdc on 2010-07-16
well done; good work;

you have put a lot of effort into an excellent guide

---

### Post by lolzwut on 2010-07-16
printers are pointless do not use them

---

### Post by Kevin_a_b on 2010-08-23
The link [http://www.downloaddelivery.com/srfilecache/CJLZ35LE-CUPS-2.0-1.TAR.GZ](http://www.downloaddelivery.com/srfilecache/CJLZ35LE-CUPS-2.0-1.TAR.GZ) seems to be broken and I can't find where to download it. Anyone knows?

---

