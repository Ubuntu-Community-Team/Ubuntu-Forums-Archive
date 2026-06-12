---
title: "Irq Issue With Junghanns Bri Card"
date: 2006-06-14
forum: Hardware &amp; Laptops
---

### Post by angyel on 2006-06-14
Hi everyone.
I am facing an IRQ problem. The problem is that my mainboard integrated network card is sharing an IRQ with a QuadBri ISDN PCI card from Junghanns. 

The system description is
A Via C3 system with the breezy badger 5.10.

The solutions i tried:
I have already tried the solution to disable almost everything in the MB BIOS (since effectively I do not need them) and in BIOS I can't assign a specific IRQ to the network card. Also I can reserve some IRQs but doin it cause both the ISDN card and that piggy network card to take another same irq together...

I have only one slot pci so I can't change it.
I have tried out a few different cards but they take differents IRQ addressing so the problem do not comes.

Can anyone tell me a solution to assign different irq to these two resources?

Thanks, Angyel

---

### Post by angyel on 2006-06-15
No one know a possible solution to my problem? crazy...

---

### Post by angyel on 2006-06-17
Just to let know the solution I have found.

typing dmesg one can see the kernel log.
In that I have seen that the HISAX module was loaded. 
To remove it i have:
1. unloaded module hisax with rmmod hisax (it told me to remove first another specific driver which i suddenly rmmod-ed) 
2. moved away the dir /lib/modules/<kernel version>/drivers/isdn/hisax 
3. modprobed the right module i had 

and all problems were gone.


Angyel

---

