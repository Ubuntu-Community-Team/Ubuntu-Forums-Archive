---
title: "Installation problem !!!"
date: 2008-08-02
forum: General Help
---

### Post by Vasilisgr on 2008-08-02
Hello to the forum , i am trying to install the ubuntu ultimate edition from the live cd to the external hard drive i have with the inter graded wizard but when i select the partition i want i get this error 

No root file system is defined.

Please correct this from the partitioning menu.

the only option that would go forward is to select the entire drive but i have a lot of data in it so i would like to install it in the partition i make.  Can any one help me with this please ? THANK you a lot :KS

---

### Post by overdrank on 2008-08-02
> **Vasilisgr said:**
> Hello to the forum , i am trying to install the ubuntu ultimate edition from the live cd to the external hard drive i have with the inter graded wizard but when i select the partition i want i get this error 

No root file system is defined.

Please correct this from the partitioning menu.

the only option that would go forward is to select the entire drive but i have a lot of data in it so i would like to install it in the partition i make.  Can any one help me with this please ? THANK you a lot :KS

Hi and when you select the partition you want then you will need to edit the partition and set it to mount as "/" this is the symbol for root.

---

### Post by Titan8990 on 2008-08-02
You have to specify to mount point of your main filesystem as "/". / is like C:\ in Windows. Don't forget about your SWAP partition.

---

### Post by Vasilisgr on 2008-08-02
thank you mate :-) another question is swap partition nececary with 2gb of ram? if yes how many gb?

thanx again

---

### Post by overdrank on 2008-08-02
> **Vasilisgr said:**
> thank you mate :-) another question is swap partition nececary with 2gb of ram? if yes how many gb?

thanx again

If you intend to hibernate or suspend then yes you will need swap.

---

### Post by Vasilisgr on 2008-08-02
Ok thank you for the support, i am a newbie so i need all the help possible :-) Your forum is the best there is THANX

---

### Post by Titan8990 on 2008-08-02
Don't forget to mark your topic as solved.

---

### Post by Vasilisgr on 2008-08-02
my friend its not solved yet.... :-) i sed newbie here :-) i mess it up.... :-( 

i did get it to install ubuntu at the partition at the external hard drive but now it refuses to boot up :-( I can boot only from dvd ... not even vista... i will post more more about it in a few i have to resatart again and copy what exactly is the error i get :-( be back in few

---

### Post by Vasilisgr on 2008-08-02
> **Vasilisgr said:**
> my friend its not solved yet.... :-) i sed newbie here :-) i mess it up.... :-( 

i did get it to install ubuntu at the partition at the external hard drive but now it refuses to boot up :-( I can boot only from dvd ... not even vista... i will post more more about it in a few i have to resatart again and copy what exactly is the error i get :-( be back in few



p.s. i did a linux partition not an ntfs ...:confused:

---

### Post by overdrank on 2008-08-02
> **Vasilisgr said:**
> my friend its not solved yet.... :-) i sed newbie here :-) i mess it up.... :-( 

i did get it to install ubuntu at the partition at the external hard drive but now it refuses to boot up :-( I can boot only from dvd ... not even vista... i will post more more about it in a few i have to resatart again and copy what exactly is the error i get :-( be back in few

It sounds like the grub did not get installed. If you are installing to a external drive this may help
[https://help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks](https://help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks)
Because the grub will need to be installed on the external drive because if you remove the drive then the system will receive the grub error.

---

### Post by Vasilisgr on 2008-08-02
I am back, when my USB hard drive is not attached i get this message : 

GRUB Loading stage 1.5.

GRUB Loading please Wait ...

Error 21 

And then freezes :confused:

BOOT ORDER Bios

Local hard drive 
cd/dvd
USB Hard Dr.
USB key 

PLEASE help :-) THANK YOU

---

### Post by Vasilisgr on 2008-08-02
thank you mate will check it out in few :-)

---

