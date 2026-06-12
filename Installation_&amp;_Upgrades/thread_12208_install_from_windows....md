---
title: "install from windows..."
date: 2005-01-22
forum: Installation &amp; Upgrades
---

### Post by maxim_86ualb2 on 2005-01-22
Ok , I got grub for Nt up and running , I got so far , now what is next... I only have one partition on my PC... & If I format it... I am sure that I will lose the downlaoded files ,is there a way to install from the net directly...

---

### Post by Tichondrius on 2005-01-22
[QUOTE=maxim_86ualb2]Ok , I got grub for Nt up and running , I got so far , now what is next... I only have one partition on my PC... & If I format it... I am sure that I will lose the downlaoded files ,is there a way to install from the net directly...[/QUOTE]
 Are saying you want to install Ubuntu, but currently you have only NT installed ?  If so, you can install Linux on the free space on your hard drive, or if there is no free space, you could resize the NT partition. To do that, first defrag the filesystem in NT. Then download and burn a Knoppix Live CD, and boot from CD. It has a tool to resize partitions - qtparted. So resize the NT partition - make it smaller. Then go on to install Ubuntu, and make sure to tell the installer you want to manually add a partition. Create it in the free space and install into that partition.

Ubuntu installer will install grub and configure it to be able to dual boot between NT and Ubuntu.

---

### Post by maxim_86ualb2 on 2005-01-23
[QUOTE=Tichondrius]Are saying you want to install Ubuntu, but currently you have only NT installed ?  If so, you can install Linux on the free space on your hard drive, or if there is no free space, you could resize the NT partition. To do that, first defrag the filesystem in NT. Then download and burn a Knoppix Live CD, and boot from CD. It has a tool to resize partitions - qtparted. So resize the NT partition - make it smaller. Then go on to install Ubuntu, and make sure to tell the installer you want to manually add a partition. Create it in the free space and install into that partition.

Ubuntu installer will install grub and configure it to be able to dual boot between NT and Ubuntu.[/QUOTE]
 hmm I didnt explain it right , I have a laptop but its floppy drive is busted... it doesnt boot from USB and there is no CD-rom.... it has a running XP system....

At this point , I resized the main partition & created a new one.... the problem is that I have no idea how to install Ubuntu from the HARDDrive..... I was wondering if ubuntu has a network installer.. as in it will load up a kernel , setup a network & download the files from a server & install them ....

---

