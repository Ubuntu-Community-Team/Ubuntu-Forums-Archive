---
title: "Can't run ATI HD 5450 on Ubuntu 9.10"
date: 2010-03-25
forum: Hardware
---

### Post by cosmoren on 2010-03-25
I have an Asus EAH5450 graphic card with HD5450 chipset.

Despite installing with Synaptic all the drivers that appear in the reppos, it doesn't work.

Somebody can help me?

(Sorry for my poor english)

---

### Post by cascade9 on 2010-03-25
Try 

System-> Administration-> Restricted Drivers Manager.

---

### Post by Yellow Pasque on 2010-03-25
Get the latest Catalyst 10.3 driver and use these instructions: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually)

Substitute Catalyst 10-3 in the commands where the guide uses Catalayst 9-12.

---

### Post by lidex on 2010-03-25
> **cosmoren said:**
> I have an Asus EAH5450 graphic card with HD5450 chipset.

Despite installing with Synaptic all the drivers that appear in the reppos, it doesn't work.

Somebody can help me?

(Sorry for my poor english)
Installing multiple drivers is never a good idea as it will cause conflicts. It seems getting ati graphics configured can be a multiple step process so no easy answer. If you want the proprietary (binary) driver go here:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

For the open source driver here:
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

It may be helpful to read through both first.

---

