---
title: "GRUB boot loader, showing not what i thought i installed"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by First on 2009-02-18
Hi, 

i`m new here, and also at any form of linux OS. SO i wanted to find out what i could do with it as a standalone computer/server for an internal network.
Now i figured out allready i needed the alternate instal (xubuntu 8.04.1) for my slow P3/665 mhz. with 128 mb.
So i installed this, since it`s recommended for slow systems.
becouse i`m new, 
i`m really sorry to bug u with an other 'newb' question.
The installation on it`s own was harder then i thought, but i got through it (anybody know a guide, which gives an explenation for every installpage?).
So i restarted as requested, and removed the instal cd.
No my GRUB boot loader only shows the memorytester.... nothing else. I don`t know how to procede... i`ve started the memtester, since it`s the only option, but will xubuntu run after this test? or did i do something wrong?

Thx

---

### Post by dakiro on 2009-02-19
I have exactly the same problem. I also had to fight a lot with the installation - it was a horror.

As to the boot loader showing useless option only, it is because (I strongly believe) that somehow there is no main kernel file (normally called vmlinuz-something), which is the, well, kernel of the system.
I am trying to find a solution to this problem but so far nocando.

the configuration of grub is placed in the menu.lst file so we need to add a stanza booting the kernel file and initrd-something file.
should look like this (example)

title Xubuntu HD
root (hd0,5)
kernel (hd0,0)/boot/vmlinuz
uuid f60b4633-4ad5-4578-8f31-996e89f3509f verbose ro splash
initrd (hd0,0)/boot/initrd.img-2.6.27-7-generic

need to find the kernel file and copy it to the appropriate location... 
Still, I don't know if this will work...

so it works - to some degree.
I copied a different kernel (older) from Ubuntu, added 
root=/dev/hdax to the kernel boot options and the system booted.
Unfortunatelly, the xserver didn't recognize my keyboard and mouse (touchpad) in console mode (ctrl+alt+Fx) keys are accepted so I don't know what it is all about. 
**[COLOR="DarkRed"]SOLVED[/COLOR]**

i solved it in the following way. The hardest point was finding the cd :) just copy the files vmlinuz and initrd.gz from /casper on the cd to your /boot folder. Then add the entries to the menu.lst file. If it won't work, add root=sdax to the stanza. Should work

---

