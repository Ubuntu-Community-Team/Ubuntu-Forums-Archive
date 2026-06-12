---
title: "Need help about partitioning my laptop + GRUB"
date: 2008-05-12
forum: Hardware
---

### Post by Gunn3r on 2008-05-12
I need a little help regarding GRUB installation.

I bought a new laptop and it brings 3 partitions, 1st is 1.4GB for recovery, 2nd is the Vista one with 112GB and 3rd is the DATA partition with 112GB also.

I was thinking in shrinking the Vista partition down to 100GB or so, redo the DATA one into 60GB and use the rest for Ubuntu root and home partitions.

I was thinking in like using this scheme:


Recovery partition -> 1.4GB
Vista --> 100GB
Vista DATA --->60 GB
/root ---> 25 GB
/home --->46 GB
Linux swap ---> 1GB

I want to use the method of installing GRUB in the Ubuntu partition and not on the MBR because I am planning to use EasyBCD to boot manage through Windows Vista, but I'm not sure how to install GRUB when it asks for hd(0,0) or something like that.
Will GRUB identify the recovery partition as hd(0,0)? In that case, would be right to say that in my scheme, Ubuntu partition will be hd(0,3) ?
Explain this to me please. I thank all the help I can get. This recovery partition is driving me nuts.

---

### Post by tubbygweilo on 2008-05-13
Please shrink any existing Vista partition from within Vista,** DO NOT** shrink a Vista partition from within the Ubuntu install process! I tried this a couple of weeks ago on my kit and spent most of the next day using the recovery partition to once more give me a working bit of kit. 

Grub should correctly identify your recovery partition, your Vista partitions and your new Ubuntu system.

May I also suggest that you set the swap partition to at least twice the size of your RAM.

---

### Post by Gunn3r on 2008-05-13
> **tubbygweilo said:**
> Please shrink any existing Vista partition from within Vista,** DO NOT** shrink a Vista partition from within the Ubuntu install process! I tried this a couple of weeks ago on my kit and spent most of the next day using the recovery partition to once more give me a working bit of kit. 

Grub should correctly identify your recovery partition, your Vista partitions and your new Ubuntu system.

May I also suggest that you set the swap partition to at least twice the size of your RAM.

Yes, I will use the Shrink feature within Windows Vista to resize it's partition. My main problem is how to identify the Ubuntu partition during Grub installation since I want it to install not on the MBR at hd0 (that role is reserved for Vista bootloader thru EasyBCD) but on Ubuntu own partiition.
I mean, Grub will identify my recovery partition right? So, what ID will it give, hd(0,0)?
Again, in my partition scheme will Ubuntu partition be identified by Grub as hd(0,3)?

I have 3gb of ram... isn't a swap with 6GB too much?

Ty for the replies and help.

---

### Post by Gunn3r on 2008-05-13
bump !

---

