---
title: "Can't install Ubuntu 64bit on hp dv6-6145dx"
date: 2012-06-08
forum: Hardware
---

### Post by m7esain on 2012-06-08
I just got HP DV6-6145dx Notebook:
  
[LIST]
[*]AMD Quad-Core A8-3500M Accelerated Processor
[*]8GB DDR3 SDRAM
[*]AMD Radeon HD 6620G
[/LIST]
  well I removed every thing that related to windows " system, hidden partitions " so that I won`t need them.
  I tried to install Ubuntu 12.04LTS 64bit and I got a lot of error and crashes:
  
[LIST]
[*]Ubuntu has an error "executable path" from the beginning after boot.
[*]Another that said Ubuntu installation process crashed
[/LIST]
  and some times the words converted to squares and can't continuing  the installation process at all.  On the other hand i tried the 32bit  version, and every thing went smoothly  
  need your help


 thanks in advance

---

### Post by arubislander on 2012-06-08
Maybe a bad image download, or maybe ubiquity (the Ubuntu installer) just doesn't like your machine. 

Fortunately you can bypass ubiquity altogether if you aren't intimidated by a text based installer, just head over to [the alternate CD]("http://www.ubuntu.com/download/desktop/alternative-downloads") section of the Ubuntu website and download the alternate CD iso...

---

### Post by m7esain on 2012-06-08
Thanks for your interest 
- i tried to download it again and got the same result , even the dvd version does the same error 
- " ubiquity " i saw that word in one of the error message, but i don't know that -doesn't like your machine- means ?? and how i can solve this issue  
- i did the alternate CD and the installation process stopped too in some point, so i skipped the error and gone to the next step, but i got the LUI

---

### Post by SeijiSensei on 2012-06-08
Does this machine have both an Intel and an ATI graphics adapter?  You may need to [flip a switch in the BIOS]("http://ubuntuforums.org/showthread.php?p=11244073#post11244073") to tell the machine to use the ATI card.

---

### Post by m7esain on 2012-06-08
No it doesn't have....

at the beginning i thought that the graphics card cause this problem, so i tried to install it using -- nomodeset -- but got the same result :(

---

### Post by m7esain on 2012-06-09
Anyone ????

---

