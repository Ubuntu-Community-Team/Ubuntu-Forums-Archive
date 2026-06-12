---
title: "Installing drivers for Lexmark X5650 printer on Lubuntu 14.04"
date: 2014-08-11
forum: Hardware
---

### Post by nadrach on 2014-08-11
I have a new Lubuntu 14.04 installation on a relatives (formerly XP) desktop. Runs fine but the printer is a Lexmark x5650 MFD. The driver package for this (lexmark-08z-series-driver-1.0-1.i386.deb) dates from 2010 (ish, I think) and has caused various bits of grief to Ubuntu users.

The Lexmark installation runs from a ".sh" script for which the Lexmark installation window is fixed in size (small) and this window is locked by an "installation failed" pop-up, which when cleared removes all the temporary files, leaving no log; so I cannot back up to find what the actual error is after it flashes past. As recommended in several threads, I have installed the libstdc++5 package, though I'm not sure if it made a difference. Eventually I managed to trap the temporary install files and extract the actual ".deb" package file and use dpkg on that. The result is an error that may be the one failing the Lexmark script install, certainly I now can just glimpse a "line 9" text message as it flashes by.

Error from dpkg is:

dpkg: error processing archive ./lexmark-08z-series-driver-1.0-1.i386.deb (--install):
 parsing file '/var/lib/dpkg/tmp.ci/control' near line 9 package 'lexmark-08z-series-driver':
 blank line in value of field 'Description'
Errors were encountered while processing:
 ./lexmark-08z-series-driver-1.0-1.i386.deb

Is there anything I can do about this since the cause appears to be in the deb package?

---

### Post by nadrach on 2014-09-05
Finally had time to use screen video capture to confirm that the error causing the Lexmark install failure is the same as with **dpkg**.
The ...deb.sh package extracts a bunch of files then runs them. Can I unwrap the package and run the extracted files manually, but get at the faulty "control" file first to see if I can fix the description? I'm not a newbie, but this would be something I have never tried before. Frankly, just getting hold of the PPD file for the x5650 from the package and installing it manually might do the trick.
Any practical suggestions entertained (apart from giving the Lexmark MFD flying lessons ... I have considered that, but at the moment a replacement is not available).

---

