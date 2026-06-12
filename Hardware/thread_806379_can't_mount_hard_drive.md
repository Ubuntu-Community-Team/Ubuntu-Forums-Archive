---
title: "can't mount hard drive"
date: 2008-05-24
forum: Hardware
---

### Post by RichInGB on 2008-05-24
I have a WD 120gb HD that's recognized in "Computer", but when I double click on it, it says "error: device /dev/hdb1 is not removable" and "error: could not execute pmount".  I have the jumper set to slave as there is a master drive already.  I'm very new to Ubuntu, so any help is appreciated.

Rich

---

### Post by mikewhatever on 2008-05-25
> **RichInGB said:**
> I have a WD 120gb HD that's recognized in "Computer", but when I double click on it, it says "error: device /dev/hdb1 is not removable" and "error: could not execute pmount".  I have the jumper set to slave as there is a master drive already.  I'm very new to Ubuntu, so any help is appreciated.

Rich

Can you post the output of <sudo fdisk -l> from Applications>Accessories>Terminal. What is on that HDD? If you use Ubuntu, partitions are usually recognized as sdX, where X is a number. It shouldn't be 'Computer', since that's a different link in Nautilus.

---

