---
title: "reinsatlling ubuntu"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by salman203 on 2009-02-26
i was running ubuntu (after repartitioning local disc C where windows was installed on my system) as a dual system alongside xp on my machine. for some reason my ubuntu got seriously damaged so that i had to delete the partition where ubuntu was installed. i regained the partition where ubuntu was installed and now it exists as a new extended drive(i named it New volume H) on my disc.
now i wanna reinstall ubuntu at the same place(New voulme H) but i dont know how to do that. Because when i run the ubuntu set-up cd it gives me me multiple options like repartitioning Local disc C or installing within windows but no option to install it at disc H. how can i reinstall ubuntu at the same old place( which is now disc H on my system)

---

### Post by Pumalite on 2009-02-26
Go 'Manual' and pick your partition.

---

### Post by salman203 on 2009-02-26
well, i selected the manual method and then the drive i want to install ubuntu in but i get the message:
" no root file system is defined"
how do i deal with it. can u please explain a little bit in detail how to do it manually.thanks

---

### Post by taurus on 2009-02-26
You pick which partition you want to reinstall Ubuntu on and you _MUST_ mount it to / or else you would get that error message.

---

### Post by salman203 on 2009-02-26
> **taurus said:**
> You pick which partition you want to reinstall Ubuntu on and you _MUST_ mount it to / or else you would get that error message.
do u mean to say that i should select the partition an then go to"edit the partition" 
alright i shall choose as u said but which file system do i choose like ext3 or ntfs or what and do i choose the "format" option as well

---

### Post by taurus on 2009-02-26
Format it to ext3.  You can't install Ubuntu on ntfs/vfat (who cares about wubi) or it will crash big time.

---

### Post by Anger 2 on 2009-02-26
Perhaps you would find the instructions on these sites helpful
[http://www.linuxnewbieguide.org/content/partitioning-disk](http://www.linuxnewbieguide.org/content/partitioning-disk)
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by salman203 on 2009-02-26
> **taurus said:**
> Format it to ext3.  You can't install Ubuntu on ntfs/vfat (who cares about wubi) or it will crash big time.
well, i installed ubuntu following all your directions. the installation system process reached to about 79% and then ubuntu desktop launched and it was all frozen.i had to force shut-down my lap-top by continued pressing on power button. i ran the cd-setup again. i tried again and it happened the same second time as well . i dont know where m i going wrong. i even checked the set-up cd for any errors and there was found no error.plz any help

---

### Post by Pumalite on 2009-02-26
Post your specs. You might also need to burn a new CD at 4x or less after doing md5sum on the iso.

---

### Post by salman203 on 2009-02-26
My specs are :
Intel pentium p-4       2 GHz
RAM                         256 MB
HD                            40 GB
current OS                Windows XP
by the way i have done a file integrity check on my set-up cd and it reported no error

---

### Post by Anger 2 on 2009-02-26
256 RAM is the minimum requirement for Ubuntu 8.10.

---

### Post by Pumalite on 2009-02-26
I recomend Xubuntu Alternate CD. You need a light Desktop.

---

### Post by salman203 on 2009-02-26
> **Pumalite said:**
> I recomend Xubuntu Alternate CD. You need a light Desktop.
i hope i m not distubing u with so many noobish questions can u plz give me the official link to download Xububtu alternate cd. Because,  what i found after search was only xubuntu codename intrepid ibex 8.10 from following link:
[http://www.xubuntu.org/get#intrepid](http://www.xubuntu.org/get#intrepid)
so, is it the same xubuntu u r talking about or is xubuntu alternate cd a different version

---

### Post by Pumalite on 2009-02-26
Better try this:
[http://cdimage.ubuntu.com/xubuntu/releases/8.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/8.10/release/)
(choose the Alternate version)

---

### Post by salman203 on 2009-02-26
> **Pumalite said:**
> Better try this:
[http://cdimage.ubuntu.com/xubuntu/releases/8.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/8.10/release/)
(choose the Alternate version)
thanks a lot for your help. i finally succeeded in installing xubuntu

---

