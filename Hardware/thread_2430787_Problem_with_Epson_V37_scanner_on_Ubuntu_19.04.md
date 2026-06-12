---
title: "Problem with Epson V37 scanner on Ubuntu 19.04"
date: 2019-11-07
forum: Hardware
---

### Post by Burt_Bicksler on 2019-11-07
I've been trying to get the Epson V37 scanner working under Ubuntu 19.04.  This was working in Linux Mint 18.x previously.  I've installed the Epson package freshly downloaded from Epson for Ubuntu 19.04.  Installed using the install script from Epson and no errors were reported.  But no scanning software recognizes the scanner.

All of the details I've been able to track down so far on line mention setting up links to the epkowa backend files.  But there is a problem, in the Ubuntu 19.04 installation there is no epkowa or any epk* directories or files to be found, and I have not been able to find any mention of how to install them.

On the old Linux Mint installation those files are present.

I've tried all the other suggestions and the sane find scanners app does see the scanner, but none of the scanning software recognizes the scanner, even after adding configurations as suggested in the sane debugging page, including adding a .hwdb file that identifies the scanner.  Now maybe I need to place that file in a different location but the one file said to add a new hwdb file under /etc/udev/hwdb.d which is where I placed the new file.

So is the epkowa backend no longer supported under Ubuntu, or is it supposedly not required?  Is this a case of the Epson imagescan package not catching up with the latest Ubuntu changes even though it claims to be for 19.04?

Has anyone else actually hit this problem and if so how did you resolve it?

Thanks,

---

### Post by Burt_Bicksler on 2019-11-07
Replying to my own question.  After posting I did a bit more digging and found some things on github related to having issues with older Epson scanners.  That wasn't a direct solution but that led me to a different Epson package which I downloaded.  Then I completely uninstalled the previous Epson scanner package for Ubuntu 19.04 and installed the newly discovered package.  This has the epkowa backend and the scanner is now working again.

Not sure how I missed this other package from Epson but it resolved the scanner issues.

---

