---
title: "toshiba issue"
date: 2009-08-20
forum: Hardware
---

### Post by jojom271 on 2009-08-20
ok i did it says kernal linux 2.6.28-15-generic  gnome 2.26.1
it aslo says that it is using 2.8 gib of memory 
processor 0: inte pent dual cpu t3400
processor 0: intel pent dual cpu t3400@2.16 ghz

how do i get it to use all 4 gib and is the processor correct?
  
toshiba sat m305 s49052 64/32 4gib 

isthis correct for ubuntu
ami doing something wrong

---

### Post by jerrrys on 2009-08-20
you usually lose some memory to upper memory,but your loosing quite a bit.

option #1; install server kernel

option #2; go to 64 bit OS

option #3; go to toshiba, see if they know any tricks

and about your processors, you have two right?  im asking because mine show up a zero and one.  what command did you use?

either go to **System Monitor** or in terminal enter **top** see if anything is using a lot of memory...

---

### Post by jojom271 on 2009-08-20
uname -a

---

### Post by jerrrys on 2009-08-20
in terminal **lshw** and that is small L

---

