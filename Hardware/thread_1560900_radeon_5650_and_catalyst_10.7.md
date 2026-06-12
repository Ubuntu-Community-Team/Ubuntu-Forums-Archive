---
title: "radeon 5650 and catalyst 10.7"
date: 2010-08-25
forum: Hardware
---

### Post by sxmaxchine on 2010-08-25
Hello i was wondering if anyone knows if the new catalyst driver (10.7) supports the ati mobility radeon 5650 graphics.

If it does what is the easiest ay to update my current driver. 

my current driver is:

(II) ATI Proprietary Linux Driver Version Identifier:8.72.11
(II) ATI Proprietary Linux Driver Release Identifier: 8.723.1                              
(II) ATI Proprietary Linux Driver Build Date: Apr  8 2010 21:40:58

All help is welcome and thanks in advance

Also when i used this command: 
lspci -nn | grep VGA
i got this result:
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc M880G [Mobility Radeon HD 4200] [1002:9712]
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc Redwood [Radeon HD 5600 Series] [1002:68c1]

Is my laptop recognizing both of them if so how am i able to use the 5600 instead of the 4200 (which i am currently using)

---

### Post by sxmaxchine on 2010-08-25
bump.

---

### Post by Yellow Pasque on 2010-08-25
Catalyst 10.8 was released today. It doesn't explicitly mention the Mobility 5650 in the release notes: [http://www2.ati.com/drivers/linux/catalyst_108_linux.pdf](http://www2.ati.com/drivers/linux/catalyst_108_linux.pdf) . You can always try it and remove it if things go poorly: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver)

---

### Post by sxmaxchine on 2010-08-26
> **Temüjin said:**
> Catalyst 10.8 was released today. It doesn't explicitly mention the Mobility 5650 in the release notes: [http://www2.ati.com/drivers/linux/catalyst_108_linux.pdf](http://www2.ati.com/drivers/linux/catalyst_108_linux.pdf) . You can always try it and remove it if things go poorly: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver)

really il have a look at it and only 1 night ago i downloaded 10.7. thanks for the reply

---

