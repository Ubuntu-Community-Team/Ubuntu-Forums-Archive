---
title: "Intel Netport Express 10/100"
date: 2008-09-24
forum: Hardware
---

### Post by doug-M on 2008-09-24
This is a follow up to an earlier thread:
Intel Netport Express 10/100
[http://ubuntuforums.org/showthread.php?t=283946](http://ubuntuforums.org/showthread.php?t=283946)

I put the IP address of the printserver in my /etc/hosts file:
192.168.1.5 hostname-of-netportexpress hostname-of-netportexpress.home.local

I had trouble before but got this to work with my Intel Netport Express 10/100 and HP LaserJet 4P on Ubuntu 8.04.

New Printer
  Other
    Enter device URI
      lpd://hostname-of-netportexpress.home.local/LPT1_PASSTHRU

Then I selected 
  HP 
    LaserJet 4P
      HP LaserJet 4P - CUPS+Gutenprint v5.0.2 Simplified [en](recommended)

---

