---
title: "HP Deskjet 3 in one unable to scan"
date: 2010-10-31
forum: Hardware
---

### Post by ubun2warrior on 2010-10-31
Hi 
I have recently purchased a HP Deskjet 1050 3 in one(print copy scan). The printer is correctly installed on ubuntu but whenever i try to scan i get the following error:-

Failed to open device 'hpaio:/usb/Deskjet_1050_j410_series?serial=...':Device busy.

(serial no is very long so just gave .... instead)

I checked on a windows machine, i was able to scan perfectly well..

I am using ubuntu 10.10 maverick desktop edition.

PLz help !!!

Regards

ubun2warrior

---

### Post by ubun2warrior on 2010-10-31
why is it not scanning ??? 
plz help...

---

### Post by franciskyong on 2010-11-12
> **ubun2warrior said:**
> Hi 
I have recently purchased a HP Deskjet 1050 3 in one(print copy scan). The printer is correctly installed on ubuntu but whenever i try to scan i get the following error:-

Failed to open device 'hpaio:/usb/Deskjet_1050_j410_series?serial=...':Device busy.

(serial no is very long so just gave .... instead)

I checked on a windows machine, i was able to scan perfectly well..

I am using ubuntu 10.10 maverick desktop edition.

PLz help !!!

Regards

ubun2warrior

I'm having the same problem with hp deskjet 1050 all- in- one in ubuntu 10.10.After running 'hp-check -r ' the following problems were reported:
1. Several  files were  not found. After installing them it was down to
2. 'user needs to be  a member of the group lp to print scan fax"
    "user needs to be a member of the group lpadmin to manage   printer"
After including user in those 2 groups and re-running 'hp-check -r' the same error message appears. I still can't scan!

---

