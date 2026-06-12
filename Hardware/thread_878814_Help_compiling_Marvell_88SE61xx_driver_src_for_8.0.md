---
title: "Help compiling Marvell 88SE61xx driver src for 8.04.1 AMD64"
date: 2008-08-03
forum: Hardware
---

### Post by BillJohnson on 2008-08-03
If this posting belongs in another forum, I apologize in advance,

I have been using early versions of ubuntu (6.06 LTS) for several years now. I just installed 8.04.1 (AMD64) on a new machine (Asus P5E3 WS Pro) and everything is mostly working (using it right now). However, I have a PATA DVD drive that is connected to a secondary controller (Marvell 88SE61xx) on the motherboard and 8.04.1 doesn't recognized or find the drive. The hardware is ok because it works on Windows XP64. Another DVD drive connected to sata works fine

So I searched everywhere and the only thing I could find on this was something about needing kernel patches for this to work. ASUS did supply linux drivers for redhat and suse, but not for ubuntu. However they did supply the source code.

Is there someone that could detail the steps necessary for me to get all of the packages necessary (kernel needs to be re-compiled), compile and install this for 64bit 8.04.1?

I have attached the readme.txt that was included with the source.

Thanks.

---

### Post by BillJohnson on 2008-08-16
Hi Bill,
This is Bill. I am sorry but there is no one on the Ubuntu forums that understands anything about how to compile a kernel, or is too busy to help you.

I would suggest going back to Windows XP 64, at least that OS supports the cutting edge hardware that you have. You should feel fortunate that you found out how the complete lack of any help from anyone is prevalent for Ubuntu systems. The old adage "You get what you pay for" seems to hold true.

---

### Post by BillJohnson on 2008-08-16
Ok Bill,
Thanks for the "heads up". I am going to throw the Ubuntu DVD's that I burned in the trash and run back to XP 64. At least I didn't waste too much time on Ubuntu before finding out how much help I could actually expect. I wasn't looking to have the answer handed to me, I just wanted some help.

I can now see why Ubuntu will never be mainstream.

Later.

---

### Post by |Eric| on 2012-03-18
the answer is that the marvell controller isnt fully suported 

here is a good place to start 
[http://en.wikipedia.org/wiki/List_of_Marvell_Technology_Group_chipsets#88SE61xx_Chipsets](http://en.wikipedia.org/wiki/List_of_Marvell_Technology_Group_chipsets#88SE61xx_Chipsets)

first compiling a kernel isnt that easy  and running with it is even more sketchy  (* the best i was able to do is compile it * ) 

there are quite a few sites where you can find the awnser  but right away i have to tell you that only the suplied driver with the proper kernel version works 100%  ( kernel 2.4 is the one that works with the asus driver) 

somehow the chipset is partially supported with pata_marvell  module
( it only finds 2 out of 4 SATA ports ) 
this is a driver issue but nor marvell nor asus nor the comunity in general seams to be interested 





if i had the necessary knowledge i would port the driver to latest kernel or somthing but im kind of lost in all that coding :P  

i figured the pata_marvell could probably be changed as to support all 4 ports on my chip 

for now i still use xubuntu but im kind of limited to 6 out of 8 sata ports its a shame the esata is one of the unsuported ports ...

edit: btw you posted this in laptop section  ... 
and i have a P5W64 WS Pro  ( 88SE6145 chipset)

---

