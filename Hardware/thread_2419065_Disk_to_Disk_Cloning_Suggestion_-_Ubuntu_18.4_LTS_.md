---
title: "Disk to Disk Cloning Suggestion - Ubuntu 18.4 LTS - IDE HDD to SATA SSD"
date: 2019-05-16
forum: Hardware
---

### Post by bullygram on 2019-05-16
Team,
I been using Ubuntu 18.4 LTS on my 40GB IDE HDD. And I wanted to upgrade to SATA SSD. I planned on using Clonezilla for disk to disk transfer. 
So my question will be, is it advisable to clone this way and run the Ubuntu without any problems, and a fresh install is not possible since it is my dev. system.
 I have seen SATA HDD to SATA SDD which is possible.

---

### Post by Claus7 on 2019-05-16
Hello,

it will work just fine. More information on how to do that can be found here:
[https://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone](https://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone)

Just a notice: the ssd drive size has to be at least that of the original disk, something that it won't be an issue taking into consideration the original disk size. Also, as it is mentioned in the guidelines, the disks should not be usable simultaneously except when the cloning procedure is taking place.

Regards!

---

### Post by rsteinmetz70112 on 2019-05-16
I have been using ddrescue to clone drives for a while. It is pretty easy and works well. It will transfer everything on the disk including any errors. :cool: 

Simply```
 sudo apt install gddrescue
``` and run ```
ddrescue
```.

Once you have cloned the drive you can expand the partitions however you want. I usually use gparted

---

### Post by SeijiSensei on 2019-05-16
I cloned the hard drive in one machine to an SSD drive. Since it was a laptop I obviously could not mount the target in the machine so I used one of these SATA to USB adaptors instead: [https://www.newegg.com/Product/Product.aspx?Item=N82E16812200155](https://www.newegg.com/Product/Product.aspx?Item=N82E16812200155)

I used ddrescue and when I was finished, I installed the clone and it booted right up.

---

### Post by bullygram on 2019-05-20
Team thanks you!
I used clonezilla to clone drive to drive. And Ubuntu ran without any issue

---

