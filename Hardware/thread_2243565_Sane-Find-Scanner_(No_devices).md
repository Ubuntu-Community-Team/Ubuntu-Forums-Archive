---
title: "Sane-Find-Scanner (No devices)"
date: 2014-09-09
forum: Hardware
---

### Post by ylafont on 2014-09-09
i am hoping someone can direct me in the proper direction.   

I am Trying to setup Fujitsu fi-4220C2 Scanner on Unbuntu 14.04, The scanner is supported by SANE however when i perform a SANE-FIND-SCANNER no devices are found. 

The Device does show up if when issuing:
scanimage -L   - which produces 


device `fujitsu:fi-4220C2dj:100742' is a FUJITSU fi-4220C2dj scanner

Also, i can preform a scan with the following:

scanimage -d fujitsu:fi-4220C2dj:100742 --format tiff -l 0 -t 0 -x 215 -y 297 > outfile.tiff

Since sane-find-scanner does not list the devices. I cannot use phpsane.     Any Assistance will be appreciated thank you.

---

### Post by rbmorse on 2014-09-10
does it give a different result if you run it as root (sudo sane-find-scanner)?

---

