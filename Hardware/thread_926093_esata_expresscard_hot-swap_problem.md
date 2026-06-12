---
title: "esata expresscard hot-swap problem"
date: 2008-09-21
forum: Hardware
---

### Post by xSauronx on 2008-09-21
I bought a rosewill rc-605 expresscard eSATA adapter for my T60, which is supported with the sata_sil24 driver, and i also have an eSATA hard drive. im using ubuntu 8.04

the card isnt hot swappable, and id like to know if i can make the card AND the drive hot-swappable

the card is supported by sata_sil24 but to use the card and the drive, they *both* must be connected during boot-up. 

interestingly, one port on the eSATA card causes a problem if its used during booth. dm_crypt starts to ask for a password for my encrypted volume, but never gets to actually ask it. using the other eSATA port solves the problem, but im not really concerned about it much. 

anyway, i have to have the card and the drive connected at boot, or they wont work. the kernel seems to see it just as a RAID controller, so it doesnt auto-mount either. 

any ideas or suggestions? googling around and searching the forums hasnt shown me any way to make the expresscard work....like an expresscard :)

---

