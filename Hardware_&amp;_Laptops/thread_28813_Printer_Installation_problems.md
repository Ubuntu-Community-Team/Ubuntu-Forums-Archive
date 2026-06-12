---
title: "Printer Installation problems"
date: 2005-04-21
forum: Hardware &amp; Laptops
---

### Post by ubuntu27 on 2005-04-21
Hi guys!! 

I am new at this community.

Anyway, I am havin problems installing my Printer in Ubuntu 5.04

I have HP Officejet 6110 all-in-one (that is Printer + Scaner + Fax + Copy)

I went to SYSTEM/ADMINISTRATION/PRINTING and I clicked on "New Printer"
It opened a windows. As you can see from the pic that I uploaded, it didn't detect my printer. 
So, I clicked on Forward. And then, I looked for HP Officejet 6110. 
Well, then, when I found it, 
I cliked on "Install Driver" and it opened a new windows, and it asked me to find a file with extention "PPD" which I don't know where to locate. 

Coould anyone help me please.

By the way I also looked to the HP Homapage, and I did NOT found driver for Linux...

---

### Post by ubuntu_demon on 2005-04-21
[www.linuxprinting.org](www.linuxprinting.org) is a very nice site

I found this for your printer :

[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-OfficeJet_6110](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-OfficeJet_6110)

they recommend the hpijs driver

$apt-cache show hpijs
$apt-cache show foomatic-filters
tells me that you have to install also foomatic-filters,foomatic-filters-ppds
also :  hplip if you have an usb printer
and hpoj if you have a parallel printer

So this should work (assuming you have an usb printer) :

$ sudo apt-get install hpijs hplip foomatic-filters foomatic-filters-ppds

After this try your new printer dialog again. And be sure to select hpijs as driver.

---

### Post by David Haas on 2005-04-21
Ubuntu27--If you are not yet used to working with shell (terminal) commands, you might prefer setting up your printer with the printer GUI. I see that the gimp-print PPD file said to work for your HP is in the Hoary distro--it's the pcl-900. In your file system it's listed as pcl-900.ppd.gz. It's located in your file system at  /usr/share/cups/model/gimp-print/4.2. You can click through the files in the printer GUI. When you select this file, it's unzipped and then listed without the gz. Make sure that you have the cupsys and foomatic packages installed, (but you won't need the cupsys-bsd) package. These are most easily found in Synaptic package manager. 
David Haas

---

### Post by ubuntu27 on 2005-04-22
heaven@heaven:~$ apt-cache show hpijs
Package: hpijs
Priority: optional
Section: text
Installed-Size: 680
Maintainer: Torsten Landschoff <torsten@debian.org>
Architecture: i386
Source: hplip (0.8.7-4)
Version: 2.0.1+0.8.7-4
Depends: libc6 (>= 2.3.2.ds1-4), libgcc1 (>= 1:4.0-0pre6ubuntu4), libstdc++5 (>=  1:3.3.4-1), gs-gpl (>= 8.01-5) | gs-esp (>= 7.07.01-8) | gs-afpl (>= 7.04-2)
Suggests: hplip | hpoj, foomatic-filters-ppds, foomatic-filters
Filename: pool/main/h/hplip/hpijs_2.0.1+0.8.7-4_i386.deb
Size: 189626
MD5sum: b18a9721a51e8c3fb4418a8fd0cd94e6
Description: HP Linux Printing and Imaging - gs IJS driver (hpijs)
 This package contains the hpijs binary which provides Ghostscript
 with a IJS driver for most inkjet printers and some LaserJet printers
 manufactured by HP.
 .
 It includes the so-called rss patch, to use pure black ink instead
 of composite black in printers that don't do color map conversion
 in firmware.
 .
 Users of USB and JetDirect HP printers are advised to also install the
 hplip package, and use the hp: CUPS backend to send data to the printer.
 Selecting any hpijs ppd in CUPS will use hpijs automatically.
 .
 Users of parallel-port HP printers are advised to install the hpoj
 package, and use it to send the hpijs output to the printer.
 .
 HPIJS is meant to be used through the foomatic system (see the
 foomatic-filters package).
 .
  Homepage: [http://hpinkjet.sourceforge.net](http://hpinkjet.sourceforge.net)
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-desktop

---

### Post by ubuntu27 on 2005-04-22
ubuntu27@ubuntu27:~$ sudo apt-get install hpijs hplip foomatic-filters foomatic-filters-ppds
Password:
Reading package lists... Done
Building dependency tree... Done
hpijs is already the newest version.
foomatic-filters is already the newest version.
foomatic-filters-ppds is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  hplip: Conflicts: foomatic-filters-ppds (< 20050114-1) but 20041013-1ubuntu1 is to be installed
E: Broken packages

---

### Post by ubuntu27 on 2005-04-22
Allright, thanks everybody. I don't know how did I did it, but it work. (I had to add a new printer and then delate it, so I can add again... I did it because it couldn't print)

---

