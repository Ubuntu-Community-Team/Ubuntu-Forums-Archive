---
title: "Promise FastTrak TX2000 IDE Controller"
date: 2005-12-22
forum: Hardware &amp; Laptops
---

### Post by Nokia555 on 2005-12-22
Hello,

I'm have trouble installing Ubuntu 5.10 server edition to my computer. It like freezes when it loads the partitsion system. Can someone help me whit that?

My machine:
Prose: Intel Xeon 2.8Ghz 
Emaplaat: E7501 Master-LM 
HDD: ExcelStor 80GB ATA/133
ATA Raid controller on: Promise FastTrak TX2000

---

### Post by Nokia555 on 2005-12-23
Somebody?

---

### Post by mabhatter on 2005-12-24
I've just got the same problem with a Rocket 133SB Card.  It hung at 41% when trying to see the hard disk on the PCI controller card.  I think I've seen something around here about it... I'll fill you in if I find it.

---

### Post by mabhatter on 2005-12-24
I think my rocket is the same or similar chipset to yours?? 

Anyway, I found that by re-arranging my cards in PCI slots it fixed the problem.  
Especially with soundblasters and other things, they can "demand" certian slots and specific irq lines no matter what the bios or os wants... one of those weird querky things... I had the same problem under windows too.


Things like IDE controllers like the "closer" pci slots... 1,2..
video cards like low numbered slots too..
Soundblasters can be really picky about being in slots 3 or 4... and hose the whole thing if they don't like their spot.
Modems and Nics tend to be the most forgiving... you can usually get away with slots at the very bottom and still be OK.

hope this helps.

---

### Post by Nokia555 on 2005-12-25
I have it on board not in PCI slots. And it dosent help if i make again the array.


[QUOTE=mabhatter]I think my rocket is the same or similar chipset to yours?? 

Anyway, I found that by re-arranging my cards in PCI slots it fixed the problem.  
Especially with soundblasters and other things, they can "demand" certian slots and specific irq lines no matter what the bios or os wants... one of those weird querky things... I had the same problem under windows too.


Things like IDE controllers like the "closer" pci slots... 1,2..
video cards like low numbered slots too..
Soundblasters can be really picky about being in slots 3 or 4... and hose the whole thing if they don't like their spot.
Modems and Nics tend to be the most forgiving... you can usually get away with slots at the very bottom and still be OK.

hope this helps.[/QUOTE]

---

### Post by heatpumpcontrol on 2007-04-28
> **Nokia555 said:**
> Hello,

I'm have trouble installing Ubuntu 5.10 server edition to my computer. It like freezes when it loads the partitsion system. Can someone help me whit that?

My machine:
Prose: Intel Xeon 2.8Ghz 
Emaplaat: E7501 Master-LM 
HDD: ExcelStor 80GB ATA/133
ATA Raid controller on: Promise FastTrak TX2000

How did you get Ubuntu installed using the Raid? Please help.

Thank you

---

### Post by siar on 2007-08-16
i'm having trouble installing ubuntu 7 server on this machine i just built with a promise tx2000 card in it with a mirror configured on it. It installs ok and then it dosent boot on the first reboot, maybe i need to check off something in the install to make it aware its going to be booting to a raid array, but its hardware raid , so i thought that the promise card would just present what looks like one hdd to linux, but during the install it lets me pick which hdd to install to, sda or sdb , which suprised me right there. perhaps i need a driver then.. [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by siar on 2007-08-16
i'm going to try 6.06 lts alternate to see if there is any difference, i read in the readme in the linux source driver for the tx2000 on the promise site that there is a problem with 2.4 kernels detecting the promise as simple ide controllers instead of raid so that might be whats happening, but it should still boot i guess..

---

### Post by siar on 2007-08-16
i gave up on this, i'm going to use an lsi megaraid card instead, i dont understand why i see 2 hard drives with this crappy card, it should be presenting one to the os, thats my understanding of hardware raid..

---

