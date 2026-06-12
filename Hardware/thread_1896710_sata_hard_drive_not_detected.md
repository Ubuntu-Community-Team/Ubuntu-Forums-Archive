---
title: "sata hard drive not detected"
date: 2011-12-17
forum: Hardware
---

### Post by micobros on 2011-12-17
Hello, 

I have a 500 Gb SATA Western Digital Caviar Hard Drive that is not detected. 
"fdisk -l" doesn't show anything for that disk. 

When i plug in another SATA hard drive (250Gb), it works fine. 
When i plug my 500Gb HD in an USB SATA Adapter and plug that onto my windows laptop, it works fine. 

Any idea?

Thanks in advance. 
Regards

---

### Post by MoreOrLess on 2011-12-17
Does the drive show in the BIOS? If not, you may need to jumper it to force SATA 150 mode. It depends on your mobo chipset.

---

### Post by micobros on 2011-12-18
I was hopping not to have this question ;) 

Actually, this BIOS is a little weird... 
I can see all IDE drives but don't know why, SATA drives are never shown. 
Even if there's a specific menu entry for "Enable SATA"

( I get same result when i plug in my other SATA disk that i do see when I "fdisk -l" under terminal... ) 


Drive Name : 
WD500AAKS
WD CAVIAR SE16 

MOBO : 
MSI K8T NEO

---

### Post by micobros on 2011-12-18
Alright, problem fixed. 

I have a VT8237 SATA chip and my SATA drive is not compatible with it. 
Except when i set OPT1 jumper to make it work in 150MB/s transfer speed. 

Everything works fine now. 

@MoreOrLess: thx for your help 

Cheers, 
mico

---

