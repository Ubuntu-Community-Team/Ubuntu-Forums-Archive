---
title: "Dual boot - Grub error 22 &amp; Error 15"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by futureal2032 on 2009-08-22
Hey i had windows XP and Ubuntu 8.10 installed

and it was working fine...

then i installed Ubuntu 9.04... While setting up...I deleted all Ubuntu 8.10 partitions..created new ones in the same space.. and installed Ubuntu 9.04.

After setup was complete... when the pc restarted.

after Loading stage 1.5...
Grub gave me Error 22

so i booted the machine from Live cd

and tried installing grub again

so i opened terminal
did this 

sudo grub
grub> find /boot/grub/stage1

then grub gives me Error 15: File not found
it does not find stage 1

it just shows error 15

can anyone help...
i need to use my computer as soon as possible

PS: I just found out my xp partition is not longer "active"

---

### Post by futureal2032 on 2009-08-22
well i has happily using 8.10 and i am regretting my decision to install 9.04.

well to remedy above grub errors i did following things

1. i used fixmbr from XP to reset mbr so i can atleast get into my XP.
2. then i reinstalled Ubuntu 9.04

Things i noticed while installing...
If i create / or /boot as a Primary partition, it shows the remaining free space as Unusable.
So i had to create Extended partitions
so i made /boot / and Swap
I chose to Install Grub on (hd0)
It did not give any errors while installing.

After restart it went straight to XP without showing Grub.

So i booted from Live cd, when i tried to find stage1 Grub gives me Error 15: FIle not found. When i tried to install grub on (Hd0) it does not give any errors..but Grub does not come up when i restart.

I did a dual boot with Ubuntu 9.04 and it installed fine there... but there also..sometimes it just hangs even before grub then when i restart it boots into grub. But on my laptop it connects to my Internet connection but does not browse (i have checked browser and network connection proxy settings, have tried connecting to different ISP's, have tried connecting directly and using wireless) It just does not browse.
It shows Ubuntu Updates list in Update Manager but does not connect to Update server/repositories or does not download any packages.

I loved Ubuntu 8.10 ...and was ahppy using it... 9.04 Sucks big time.

---

### Post by futureal2032 on 2009-08-24
Solved this particular problem

---

### Post by hamilyon on 2009-10-27
> Solved this particular problem 

Expiriencing the same problem. Please explain how did you get it to work.

---

