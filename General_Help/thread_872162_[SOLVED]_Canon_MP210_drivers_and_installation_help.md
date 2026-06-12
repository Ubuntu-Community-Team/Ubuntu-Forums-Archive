---
title: "[SOLVED] Canon MP210 drivers and installation help please"
date: 2008-07-27
forum: General Help
---

### Post by cowboyup6983 on 2008-07-27
so i've been using Ubuntu for about a week now, and I'm loving it. I wish I new sooner, instead of going through all the nightmares with vista. 

my only on-going problem with ubuntu is i cannot get my printer/scanner to work. ive gone to the Australian site of Canon and there are linux drivers for my model number but im not exactly sure which to pick, and how after its downloaded on my desktop, what i have to do to install.

here is a link to the page with 10 different drivers, 
[http://support-au.canon.com.au/EN/search?v%3aproject=ABS-EN&binning-state=model%3d%3dPIXMA%20MP210%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&](http://support-au.canon.com.au/EN/search?v%3aproject=ABS-EN&binning-state=model%3d%3dPIXMA%20MP210%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&)

please if anyone can take a look at the link and let me know what they think is the best way to go. by the way i have a CANON MP210 printer all-in-one.

---

### Post by naildeca on 2008-07-27
I recently istalled drivers for my Canon printer (a different model).

I believe you need these two files,
IJ Printer Driver Ver. 2.80 for Linux(debian Common package)
and
IJ Printer Driver Ver. 2.80 for Linux(debian Package for the MP210 series)

The download button is a the bottom of the page of "terms and conditions" and license to read. After checking the box saying you have read, etc. A "Download" button appears.

Downloaded both files and save them to the desktop.

The printer should be on connected to the computer. Then the common package should be installed first (double click in the icon and the installer, gdebi, begins)

Then do the same for the MP210 file.

Then you can go to System -> Administration -> Printng and add your printer.

Good luck.

---

### Post by cowboyup6983 on 2008-07-27
> **naildeca said:**
> I recently istalled drivers for my Canon printer (a different model).

I believe you need these two files,
IJ Printer Driver Ver. 2.80 for Linux(debian Common package)
and
IJ Printer Driver Ver. 2.80 for Linux(debian Package for the MP210 series)

The download button is a the bottom of the page of "terms and conditions" and license to read. After checking the box saying you have read, etc. A "Download" button appears.

Downloaded both files and save them to the desktop.

The printer should be on connected to the computer. Then the common package should be installed first (double click in the icon and the installer, gdebi, begins)

Then do the same for the MP210 file.

Then you can go to System -> Administration -> Printng and add your printer.

Good luck.

thanks for responding. after i double click the common package, i got an error message "wrong architecture i368.

im using ubuntu 64bit, cause i have over 4GB of RAM. any recommendations

---

### Post by cowboyup6983 on 2008-07-30
> **cowboyup6983 said:**
> thanks for responding. after i double click the common package, i got an error message "wrong architecture i368.

im using ubuntu 64bit, cause i have over 4GB of RAM. any recommendations

anyone has any recommendations i need to find some linux x64 bit drivers for my canon mp210 printer. i need to print some docs in a couple of days. anyone else out there have ubuntu 8.04 x64 that can recommend anything new, or now of a printer that will definitely work with my system.

---

### Post by cowboyup6983 on 2008-07-31
i reinstall ubuntu using x32bit, the above instructions are correct and my problem is now sloved. thanks to all for the help

---

### Post by pucenavel on 2008-09-27
Thanks - I'd been having trouble finding the correct link via Canon.

---

### Post by netof_100 on 2008-11-11
thanks for the information, but that is only for the printer how about the scanner functionallity, does anyone know how to make the scanner to work in ubuntu 8.10???

---

### Post by bmpv666 on 2008-11-22
> **netof_100 said:**
> thanks for the information, but that is only for the printer how about the scanner functionallity, does anyone know how to make the scanner to work in ubuntu 8.10???

for me worked out of the box with XSane! have you tried that?

---

