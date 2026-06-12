---
title: "Epson WF-2630 USB printer not working"
date: 2018-04-06
forum: Hardware
---

### Post by jg-jguk on 2018-04-06
Hello, Running fresh install of Ubuntu 64bit (this printer was working ok on my previous install of same latest Ubuntu)

Any ideas?

[FONT=&quot]
[/FONT] # dpkg -i epson-inkjet-printer-escpr_1.4.1-1lsb3.2_amd64.deb 
Selecting previously unselected package epson-inkjet-printer-escpr.
(Reading database ... 220571 files and directories currently installed.)
Preparing to unpack epson-inkjet-printer-escpr_1.4.1-1lsb3.2_amd64.deb ...
Unpacking epson-inkjet-printer-escpr (1.4.1-1lsb3.2) ...
dpkg: dependency problems prevent configuration of epson-inkjet-printer-escpr:
 epson-inkjet-printer-escpr depends on lsb (>= 3.2); however:
  Package lsb is not installed.


dpkg: error processing package epson-inkjet-printer-escpr (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 epson-inkjet-printer-escpr


[FONT=&quot]

Saw this old thread

[/FONT]https://ubuntuforums.org/showthread.php?t=2277556

  # apt-cache policy lsblsb:
  Installed: (none)
  Candidate: 9.20160110ubuntu0.2
  Version table:
     9.20160110ubuntu0.2 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages



[FONT=&quot]
[/FONT] [FONT=&quot]
[/FONT]

---

### Post by jg-jguk on 2018-04-06
Update manager crashed, because of this error. It advised to do this.

apt-get install -f

After that the printer coudl be added ok from System Settings. So seems to be working now. Wish Epson would fix the official package though.

---

