---
title: "grub install problem on Sata disk"
date: 2006-01-11
forum: Installation &amp; Upgrades
---

### Post by edistar on 2006-01-11
Hello!

I hope you can help me:
I bought a WD 160 GB Sata HDD and tried to install Breezy on it..
It goes through everything but at the end it does not install grub, it just stays at 0% :(
What can it be?

It can't be a broken cd because I had installed Breezy onto the IDE HDD before...

My system:
AMD 3800+ X2
SN25P Shuttle barebone (nvidia4 ultra chipset)
WD Caviar 160 GB Sata
NEC 3500a DVD-writer

Regards,
Edwin

---

### Post by Kipper on 2006-01-11
Has the SATA drive just been added to a system alongside an existing PATA drive? What is the first boot drive in your BIOS set to? Did you do an expert or standard install? How did you use the partitioner? How did you use the GRUB bootloader option?

Do you have a Live CD? If so, I would run it and see if your new hardware set-up is detected and is fully functional, particularly if the SATA drive is recognised.

---

### Post by edistar on 2006-01-11
I installed the new HDD and resetted the BIOS. Then I made sure it was listed as the only drive in the pc.... So that is not the problem.
I used a standard install, I don't know if I could complete an expert install ;)
I only have one drive and I do not want to dual boot etc. so I had the installer format the entire disk and put the 2 partitions on, like it suggested.
I think my HDD is detected as it can format and install ubuntu! only at the end when it is supposed to install grub in can't...
Thanks for helping...
Greetings,
Edwin

---

### Post by Kipper on 2006-01-11
Edwin,

Ok, I don't know why the GRUB installer should stall on you. The Ubuntu installer  use the "grub-install" command to do this and it is possilbe for some reason it cannot see your SATA drive. 

To get past this block, I would suggest this. Use an expert install. Believe me, you don't have to be an expert to do this. Most of the time you just choose the defaults and most of the things are the same as the standard install. But once you get past partitioning your disk and adding users. You get the option to install GRUB on a floppy disk, or use the alterntaive bootloader "lilo". Infact you can do both things by using the "go back" command. Then hopefully your install will proceed as normal.

I have assumed your system still has a floppy drive. Good luck..

---

### Post by mba on 2006-01-11
Hello Edwin,

I had too this problem.

I resolve it installing Ubuntu by the expert mode.

I can notice that after the step of 'copiing remaining file from cd' the installer step over the step of 'creation of user'.

Be sure before to install Grub that you have init root password and create a user account.

Sory for my english :D

---

### Post by edistar on 2006-01-12
Hey!
Thanks for telling me to use expert mode! It all works now......
Strangely enough it could write grub to HDD in expert mode...

Regards,
Edwin

---

