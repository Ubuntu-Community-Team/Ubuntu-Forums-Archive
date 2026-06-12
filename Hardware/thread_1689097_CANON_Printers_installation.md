---
title: "CANON Printers installation"
date: 2011-02-16
forum: Hardware
---

### Post by this_costs_more_cell_bill on 2011-02-16
Some of us installed a Linux distro AFTER already bought some hardware and we won't just throw away our equipments not supported for Linux. In this category of hardware is the CANON equipment.
As CANON doesn't care about Linux users (posting an obsolete "Linux driver" on their website), I think UbuntuForums should make people aware about necessary steps when installing any Canon printer:

1) try to obtain any type of "Linux driver" for you Canon printer - which would be a RPM file or a TAR.GZ file - directly from Canon website or - if Canon doesn't even list a "Linux driver" for your Canon printer - then anywhere else Google shows you. Try to obtain the RPM 
(check inside the TAR file if that's what you got) file with the filename containing the exactly same printer model you have. E.g.: Canon website might give you "IP1500" driver for your IP1000 printer. I wouldn't trust Canon website so much as they don't care about Linux users. Really. But still, for a Canon printer, it's the first place where I would try a "Linux driver" from.

2) if you got a TAR file at the previous step, extract its content in a folder, cause it's the RPM file inside it that we are looking for. For every single RPM file, run this command in terminal in order to transform it in a .DEB file (Ubuntu belong to the Debian family so it's .DEB files that you should expect to work):
**alien -k your-driver-for-CANON-printer.rpm**
Why -k option? Just because, by default, alien adds one to the minor version number of each package it converts. If this option is given, alien will not do this.

3) When trying to install de DEB file, you might be warned about  missing packages. There is a particulary one missing package that I  wouldn't try to obtain - **libcupsys2**, as it's CANON's fault they're not using the  correct package (they should use **libcups2**).
3.1) for each and every DEB file obtained at step 2, check for a mention of **libcupsys2** in the text of any file inside the DEB archive. Usually it should be only **./DEBIAN/control** file that is using this **libcupsys2** package reference.
3.2) inside to directory where your .DEB files are, run in Terminal these commands that will unpack the DEB archive:
**dpkg-deb -x your-driver-for-CANON-printer_file1.deb file1**
**dpkg-deb --control ****your-driver-for-CANON-printer_file1****.deb**
3.3) edit the **control **file from **DEBIAN **folder, changing **libcupsys2** with **libcups2**
3.4) move **DEBIAN **folder with the modified control file inside [B]file1
[/B]3.5) repackage **your-driver-for-CANON-printer_file1.deb** using the changed content:
**dpkg -b file1 ****your-driver-for-CANON-printer_file1**[B].deb
[/B]3.6) repeat these steps for every DEB files you have for your printer.

4) When trying to install de DEB file, you might still be warned about missing packages; for some unknown reason, missing packages considered "deprecated" or "obsolete" by Ubuntu developers (but still used by CANON "Linux drivers") don't show up using standard repositories and I couldn't figure out what repository should be added in order to get any missing package with **sudo apt-get install**, but they are available from this website ***[http://packages.ubuntu.com/dapper/libglib1.2](http://packages.ubuntu.com/dapper/libglib1.2)***
Just write the missing package name in the search box in the top-right side of the webpage and then you have it in just 3 steps.

5) CUPS is really annoying but this is it: it expects **/usr/lib/cups/filter/pstocanonbj** file to be owned by the root and only by the root (yes, not by any other user with root privileges like we are all using). So you'll have to do this in terminal:
**sudo chown root:root /usr/lib/cups/filter/pstocanonbj**

6) if it still doesn't work, then retry other "Linux driver" for your CANON printer from step 1.


Please correct me if I'm wrong, and I'll modify this message. Thanks.

---

### Post by Al-Man on 2011-04-14
Thank you.for your guide, Step 5 was the clincher for me.

---

