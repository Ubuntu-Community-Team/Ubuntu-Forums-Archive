---
title: "DMRAID still not supporting AMD chipsets?"
date: 2010-09-18
forum: Hardware
---

### Post by alraz on 2010-09-18
Hello.

I've been waiting for years now for Ubuntu tu suppord AMD chipset's fake RAID.

I once had an nVidia controller and my fake raid worked perfectly; but since a few years, when I updated to an AMD chipset based motherboar, dmraid has refued to work at all. Not ubuntu 9, not 10, not even in the new 10.10 beta.

I have a RAID 5 configuration with 3 1.5TB disks. But I'v also tried with 3 320GB disks in RAID 0 and RAID 5 and none of them worked.

for now, on ubuntu 10.10 beta, im getting the following error:
alraz@alraz-desktop:~$ sudo dmraid -r
[sudo] password for alraz: 
ERROR: pdc: zero sectors on /dev/sdd
ERROR: pdc: setting up RAID device /dev/sdd
ERROR: pdc: zero sectors on /dev/sdc
ERROR: pdc: setting up RAID device /dev/sdc
ERROR: pdc: zero sectors on /dev/sdb
ERROR: pdc: setting up RAID device /dev/sdb
no raid disks


Even though the RAID works just perfectly on windows. Can somebody give me a light on this topic?

---

### Post by ronparent on 2010-09-19
Dmraid does not support a raid 5 level on the promise fakeraid chipset (what AMD is using per the pdc designation). I have a gigbyte MB with the same raid chipset and share your frustration.

---

