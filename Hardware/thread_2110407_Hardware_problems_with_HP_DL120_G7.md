---
title: "Hardware problems with HP DL120 G7"
date: 2013-01-30
forum: Hardware
---

### Post by mmiat on 2013-01-30
Hi to all
I've tried to install Ubuntu Server 12.04LTS on DL120. Before doing it, I've found this server is certified: [http://www.ubuntu.com/certification/hardware/201107-8315/](http://www.ubuntu.com/certification/hardware/201107-8315/), but:
1) raid doesn't work, it's a fake raid and HP drivers are only for RE and SUSE
2) cpu fan speed is 100% all the time
3) if I halt system the server doesn't shut down but remains with "system halted" message
I don't think this is normal in a CERTIFIED hardware, so or I was wrong or Canonical was....
Thanks

---

### Post by ronparent on 2013-01-30
A true fakeRAID array is usually accessed in a Linux system with dmraid rather than a driver per se. If dmraid is not already installed you can install it and in a terminal enter the command: > sudo dmraid -ay 
Note that the raid has to be turned on in bios and the raid bios has to be used to initiate the raid structure on the drives selected to be part of the raid. Only after that can they be accessed for partitioning, etc. Also unless the raid has to be access by Windows in a side by side installation, a Linux software raid could better serve you.

---

### Post by mmiat on 2013-02-12
it returns me "no raid disks", it means that it isn't supported by dmraid? thanks

---

