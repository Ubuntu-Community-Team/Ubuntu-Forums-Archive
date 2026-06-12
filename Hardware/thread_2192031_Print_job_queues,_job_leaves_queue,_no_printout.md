---
title: "Print job queues, job leaves queue, no printout"
date: 2013-12-05
forum: Hardware
---

### Post by Old_Brewer on 2013-12-05
Hi All
I just added a HP Deskjet 2514 printer to my Ubuntu 10.04 (lucid), Dell B130 laptop.  The test page job shows up in the queue, leaves the queue, (shows as completed), but nothing prints.  I have the old printer, set up to print via the wireless network, through a print server.  The old printer works, the new printer does not.  The troubleshooting file that I generated exceeds the upload limit for this forum, so it is attached as:  HP_2514_lp_troubleshoot.txt.tar.gz
This is a all-in-one printer.  I can make copies, so I think the basic hardware is good.  I can take the printer to a Vista computer & make sure it prints from a Windows environment.  Also the printer is a supported printer:
[http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_2510_series.html](http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_2510_series.html)
I followed the on screen GUI setup, not the setup found here:
[https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne)
All help will be appreciated.  Thanks

---

### Post by ajgreeny on 2013-12-05
Did you actually install the latest hplip version or are you still on the version in the 12.04 repos?

Unfortunately the repository version for 10.04 is too old and the minimum version required for that printer is 3.12.6, so you will have to get the newest **hplip-*version*.run **file and follow the instructions to install it which are at [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html), though that may no lo0nger be possible as the repos for 10.04 desktop version may no longer be available, though the server version repos should be.  Whether the needed packages to run the installation procedure will still be available is something I can not give you an answer to, I'm afraid.

---

### Post by Old_Brewer on 2013-12-05
Thanks for the help.  I installed HPLIP 3.13.11.  I can print.  Next is trying to scan.
Thanks again for the help:D:D:D

---

