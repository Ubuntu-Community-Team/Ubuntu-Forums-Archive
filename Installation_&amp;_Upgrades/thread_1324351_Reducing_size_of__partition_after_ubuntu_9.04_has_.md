---
title: "Reducing size of / partition after ubuntu 9.04 has been installed?"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by shriniketsarkar on 2009-11-12
Hi I have installed ubuntu 9.04 on my DELL 1320 laptop.
As needed that time i had installed it on the entire disk and now i need to make a separate drive out of the free space. 
Is it possible to resize the root partition of this installed ubuntu so that i could make an additional drive of say 10Gb out of the unused 106gb?

Does this solution work :
        Booting form the live cd and then using Gparted to resize the root partition directly ..... and then removing the CD and booting from the installed ubuntu OS ? Will the OS crash or not ?
Regards, 
Shriniket Sarkar

---

### Post by viralmeme on 2009-11-12
> **shriniketsarkar said:**
>  ..
Does this solution work :
        Booting form the live cd and then using Gparted to resize the root partition directly ..... and then removing the CD and booting from the installed ubuntu OS ? Will the OS crash or not ?
Regards, 
Shriniket Sarkar
That should work ..

---

### Post by wojox on 2009-11-12
> **ymitchell said:**
> That should work ..

I second that.

---

### Post by cariboo on 2009-11-12
Just don't get impatient, as it may take quite a while.

---

### Post by shriniketsarkar on 2009-11-12
> **ymitchell said:**
> That should work ..

Where does Ubuntu keep track of partitions .....or does it recalculates all the partitions on every boot from the actual size available ?

Because if i carry out the method that i talked about which you guys backed me up on ......is there a possibility that ubuntu may detect the change in the root partition size and may object the change ? 
So any idea about how does it keep track of the sizes of the partitions?
Regards, 
Shriniket Sarkar

---

