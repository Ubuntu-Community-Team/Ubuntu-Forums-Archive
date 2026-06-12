---
title: "Laptop Asus A6R problems"
date: 2006-09-05
forum: Hardware &amp; Laptops
---

### Post by conqueror on 2006-09-05
Hi all, any one can help me in installing KUBUNTU on my laptop Asus A6R perfectly. Because I face many problems in configuring my graphic card, wireless card, hotkeys. Thank you

---

### Post by arkangel on 2006-09-05
I have an A6V   what are your spec  that might help 
exaclty  waht problems are you facing ?

---

### Post by conqueror on 2006-09-05
For wireless card the Kubuntu detects it but can't work. and the graphic card also. I tried to configure wireless as it described in the forum but it didn't work.

---

### Post by conqueror on 2006-09-05
My chipset is ATI radeon xpress 200m, I saw many persons faced problems with ATI.

---

### Post by arkangel on 2006-09-06
Nasty  business

you probably have read here
[http://ubuntuforums.org/showthread.php?t=204910&highlight=X200](http://ubuntuforums.org/showthread.php?t=204910&highlight=X200)

i have an Ati X700  and i was installing the driver  as described in the wiki, and never worked ,  one day i just run the driver as it comes from the ati site 
sudo sh  [ati_driver_name].run

and worked perfectly (you can try ) using the 8.28.8 now 

i have this  wireless card  PRO/Wireless 2200BG included in the centrino pack worked out of the box

just in case [http://www.marcussmit.nl/linux-on-laptops/asus_a6r_fc5.html](http://www.marcussmit.nl/linux-on-laptops/asus_a6r_fc5.html)

I thought A6R and A6V were more similar  good luck  in case i find out something else i will post

---

### Post by mario_7 on 2006-09-10
I have Asus A6Rp laptop and hotkeys are working (except touchpad on/off one) without additional configuration (but on the newest kernel, don't forget about asus laptops acpi extras).

Check lspci for the name and model of your wireless card. If you have Broadcom wireless card based on BCM4318 here is solution: [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

