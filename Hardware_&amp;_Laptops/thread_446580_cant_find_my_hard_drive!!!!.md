---
title: "cant find my hard drive!!!!"
date: 2007-05-17
forum: Hardware &amp; Laptops
---

### Post by ninjaprawn on 2007-05-17
hi,

i had ubuntu feisty on a dual boot with winxp, i then used gparted, formated what used to be my c:\ drive to ext3 and updated my grub. ok

the problem is, that i had an icon on my desktop. but now, i cant access it atall!! 

in nautilus, it used to be listed on the left in the tree! its just completely disappeared!!!!!!!

how do i get it back??

thanks

---

### Post by RyanVanDiemen on 2007-05-17
I assume you are aware of the fact that you lost your data on your windows partition. 

Firstly, you need to find out which partition it is
In command line write

sudo fdisk -l 

Identify the partition you`re talking about, create a folder you want to mount to (any for example /home/yourhomefolder/formerlywindowspartition

and then just mount it

sudo mount /dev/sdaN /home/yourhomefolder/formerlywindowspartition

where sdaN is partition you need to mount (probably the first partition on your disc, in that case sda1)

and it should be mounted. Icon should be on your desktop, if it`s not you will find the content of the disc in the folder you mounted into

I hope it helps

---

### Post by ninjaprawn on 2007-05-17
thanks!

that sounds good to me! ill try when i get home in a bit!

---

