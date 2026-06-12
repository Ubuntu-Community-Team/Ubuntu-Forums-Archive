---
title: "[SOLVED] Printer HP LaserJet 1018 does not work in Intrepid Ibex"
date: 2008-11-11
forum: Hardware
---

### Post by dobri on 2008-11-11
I've been using HP LaserJet 1018 for 6 months. It worked fine in Ubuntu 8.04. Several weeks ago I reinstalled Ubuntu 8.04 and after that upgraded to Ibex. Now the printer HP 1018 is recognized but it won't print anything.

This errors are logged when I try to print a page:

```

File : /var/log/cups/error_log

ltdb: tdb((null)): tdb_open_ex: could not open file /var/lib/samba/group_mapping.ldb: Permission denied
Unable to open tdb '/var/lib/samba/group_mapping.ldb'
Failed to connect to '/var/lib/samba/group_mapping.ldb'

Unable to create job status pipes - Too many open files.
Unable to create job filter pipes - Too many open files.
Unable to save subscriptions.conf - Too many open files.

```

This is /etc/cups/printers.conf
```

File : /etc/cups/printers.conf
# Printer configuration file for CUPS v1.3.9
# Written by cupsd on 2008-11-11 12:00
<DefaultPrinter HP-LaserJet-1018>
Info Hewlett-Packard HP LaserJet 1018
Location mycomputername
DeviceURI hp:/usb/HP_LaserJet_1018?serial=KP2X2KZ
State Idle
StateTime 1226397608
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

```

Any help will be appreciated!

---

### Post by dobri on 2008-11-13
Solved! I found the solution in this thread : [http://ubuntuforums.org/showthread.php?t=964623](http://ubuntuforums.org/showthread.php?t=964623)

I followed the suggested steps :
> 
To fix it:
1) Install hplip-gui: sudo apt-get install hplip-gui
2) Remove/Delete your current printer setup in System > Administration > Printing
3) Set up the printer again: sudo hp-setup
(It's mostly next > next > next - Be sure to have internet connection available)
4) Make sure the username is in lpadmin and scanner groups:
sudo adduser $USER lpadmin
sudo adduser $USER scanner
5) After you've done all this, switch off the printer, reboot your machine and switch on the printer once more.
It should be working now 


Special thanks to spiderbatdad and mdurham.

---

### Post by loolee on 2009-02-15
thanks!!

---

