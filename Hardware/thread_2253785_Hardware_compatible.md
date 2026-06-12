---
title: "Hardware compatible?"
date: 2014-11-22
forum: Hardware
---

### Post by vinicius8 on 2014-11-22
Hi I have an Asus Motherboard H87M-PLUS 4th generation LGA 1150 socket
chipset Intel H87 Express chipset


8111G Realtek Gigabit Lan


Audio Realtek ALC 887


Processor Intel Core I5 4430


Graphics Card Nvidia Geforce GTX 650


I want to know if they are compatible with Ubuntu 14.04.1 desktop


from and thanks for the info

---

### Post by bashiergui on 2014-11-22
Check your hardware against this list
[http://www.ubuntu.com/certification/desktop/](http://www.ubuntu.com/certification/desktop/)

---

### Post by mörgæs on 2014-11-22
Chances are good that it's fully compatible. Best is to try a live boot before proceeding.

Hardware does not have to be certified in order to be compatible.

---

### Post by grahammechanical on 2014-11-22
You will also need RAM in that machine. :)

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Regards.

---

### Post by oldfred on 2014-11-22
It should work.

But I just installed to a new Asus Z97-AR card. And to get it to boot in UEFI mode required many settings to be changed in UEFI. And a UEFI update.

You probably will need nomodeset to get video to work correctly with the nVidia card and install the nVidia driver from Ubuntu repository. You should not need the very newest driver directly from nVidia and that requires updates separately with every kernel update where repository install does the updates automatically.

       Asus Motherboard Change UEFI from Windows (secure boot only) to other OS
[http://ubuntuforums.org/showthread.php?t=2245911](http://ubuntuforums.org/showthread.php?t=2245911)
Minor problems with using an ASUS Z97-A Motherboard
[http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard](http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard)

 ASUS Rampage IV Extreme motherboard
[http://ubuntuforums.org/showthread.php?t=2063073](http://ubuntuforums.org/showthread.php?t=2063073)

The 97 series is a minor refresh over the 87 series and is usually very similar otherwise.

---

