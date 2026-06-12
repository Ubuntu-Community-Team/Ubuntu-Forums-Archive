---
title: "Win 7 / Ubuntu 9.04 headaches"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by Tickle on 2009-05-11
I installed Win 7 RC saturday and was hoping I could dual-boot Ubutu 9.04 so I could try em both out. Wishful thinking. My machine is set up this way: Drive 0 is a 250Gig PATA drive and drive 1 is a 250Gig SATA drive connected to a Silicon Image SATA PCI card (old pc). This is what i can remember trying:

Win 7 drive 0, Ubuntu drive 1, grub on drive 0 - never popped up

Win 7 drive 0, Ubuntu  drive 1, grub on drive 1 - never popped up

Win 7 drive 0, Ubuntu drive 1, grub on win boot partition - kill all installs

Win 7 drive 0, Ubuntu free space drive 0, grub drive 0 - never popped up

Win 7 drive 0, Ubuntu free space drive 0, grub boot partition - killed all installs

tried using Easybcd 1.7.2 with several of the combinations and never could get Ubuntu to boot 

am i missing something?

Any help would be greatly appreciated. I have searched the forums and have tried the solutions I have found.

As a side note - I've never had these problems with vista/xp/ubuntu multiboot installations before :(

---

### Post by Tickle on 2009-05-11
Good News. I am replying to my own post from my Ubuntu install :)

Apparently grub is freaking out for some reason. Here is my final solution:

Reinstalled Win 7

Reinstalled Ubuntu on the SI controller drive using the "use largest free space" option.

Installed EasyBCD 2.0 beta in Win 7

Added Neogrub to the menu and configured it with these lines - 

title   Ubuntu 9.04
root    (hd0,1)
kernel  /boot/vmlinuz-2.6.28-11-generic root=/dev/sda1
initrd  /boot/initrd.img-2.6.28-11-generic


I didn't add an entry for win 7 as this would be very redundant. Reviewing my other post it appears that Ubuntu is seeing the SI drive as drive 0 and the PATA drive connected to the motherboard as drive 1. Here's a good lesson for all new people - keep good notes :) They helped me finally fix my own problem!! Now to have some fun....Starcraft in Ubuntu anyone?

---

