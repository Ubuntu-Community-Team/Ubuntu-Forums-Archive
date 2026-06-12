---
title: "( Half RAM ISSUE or less than original DIMMs)  RAM Detection Issues in Ubuntu 16.xx"
date: 2017-08-18
forum: Hardware
---

### Post by ag17india on 2017-08-18
My system has a fresh install of Ubuntu 16, after WIN 10.

It only shows half the RAM as detected. They are in Diff DIMMs and seemed to be detected fine by my Windows OS. Also i get Swap as 2GB it may sound silly but is the RAM being reffered to as 

SWAP memory?? Highly unlikely as it is, swap to the best of my know how is like VRAM or a page file of linux aka Virtual file on our HDD.....but its odd its the same size as the missing RAM.


Anyone facing similar issues can report here and any senior authority or knowledgeable troubleshooters may assist kindly. Much appreciated.


Issue : RAM - 4GB in 2 DIMM slots, only 2GB detected.  
2GBx2 
Manufacturer - TRANSCEND

Specs: 

Eveything else runs fine. 
Processor : AMD SEMPRON 145 (2.8GHz) 
GPU : Nvidia GT 610 (2 GB)
HDD : 500GB 
Ram clock speed : 590 mhz
PSU powers all components no power issues 450-500Watt PSU.
BIOS - flashed for latest version i am to believe. 
*Re-insterted RAM sticks by removing them and reinserting. Still problem persists. No dust issues.
*UBUNTU version 16.0.4 LTS (XENIAL) 
CPU and other Temperatures - 35-39 Degrees (Celcius) (Stable) 
Motherboard : ASROCK N68-VGS3 FX

---

### Post by Autodave on 2017-08-18
The swap file is a set aside amount on your HD in case that your RAM becomes full and needs to unload part of itself. The swap file will generally be equivalent to the amount of RAM installed in the PC.

What does it show in the BIOS as amount of RAM available? Are the 2 sticks matching exactly?  Are you sure that they are inserted in the proper slots?

---

### Post by oldos2er on 2017-08-19
Thread moved to *Hardware*

---

### Post by Bucky Ball on 2017-08-19
Are you using the 32bit or 64bit version of Ubuntu?

---

