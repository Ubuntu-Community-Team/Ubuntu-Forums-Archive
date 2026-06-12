---
title: "lexmark printer stop working"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by kelt58 on 2009-11-11
My Lexmark X2690 printer was working before I upgraded from 9.04 to 9.10, now it isn't. This is a three in one printer. I am able to scan things using Xsane perfectly. but unable to print a test page or anything else. I think as a printer it is not communicating with CUPS. I have tried to reinstalling the lexmark driver "lexmark-inkjet-08-driver-1.0-1.i386.deb.sh" and that doesn't seem to help.  Is there any advice out there

---

### Post by loowens on 2009-11-13
I am having the same issue with a Lexmark x2600 all-in-one.  Worked fine under 9.04, but stopped printing after upgrade to 9.10.  Any help would be appreciated.

---

### Post by ian.patient on 2009-11-20
I too had problems after upgrading to Ubuntu 9.10
My Lexmark X1270 stopped printing: having tried to print something, a file or a test page, the "Document Print Status" window said that the print job was stopped. I think there were two problems:

1) **The printer driver was not owned by root**. This information was gleaned from the printer diagnostic messages when following the trouble-shooter offered at some point. Fixed with the following in a terminal (menu Applications / Accessories / Terminal), and supplying my password when asked. You will need to substitute the name of your printer driver for rastertoz600: the trouble-shooter will give some idea.
```
sudo chown root:root /usr/lib/cups/filter/rastertoz600
```This did not, however, fix the problem, but it did change the error messages.

I did actually try purging cups from my system and reinstalling, so that any configuration files would be reset, but this did not cure the problem.

I also found that / and /lib (or was it /usr ?) were also not owned by root, so I fixed them too. Not sure if that was relevant.

2)** The printer driver did not run** (it is, after all, an executable). I discovered this when I looked at printer operations by visiting [http://localhost:631/](http://localhost:631/) with my browser. This is a standard CUPS thing. Navigating to my printer queue, I saw the stopped print job and an error message under it about rastertoz600. Next I ran the printer driver in a terminal, with no arguments, using
```
/usr/lib/cups/filter/rastertoz600
```This is an odd thing to do, but I can't see that it is dangerous unless you accidentally run something else...
Anyway, the OS gave an error message about a **missing library**:
```
username@computername:/usr/lib/cups/filter$ ./rastertoz600
./rastertoz600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```I couldn't find a deb package that would supply the library in a straightforward Ubuntu way, but that's probably because I have very primitive ideas about installation. I found some rpm which, when opened with archive manager (right click on saved rpm file, open with archive Manager), obviously had the files in. I extracted these to the desktop and installed them with
```
sudo cp ~/Desktop/libstdc++.so.5.0.7 /lib
sudo chown root:root /lib/libstdc++.so.5.0.7
sudo ln -s /lib/libstdc++.so.5.0.7 /lib/libstdc++.so.5
sudo ldconfig
```And suddenly the printer worked ;)

---

