---
title: "GUI fails to load, issues on install"
date: 2006-02-05
forum: Installation &amp; Upgrades
---

### Post by sfdxsm on 2006-02-05
Hey guys, I'm fairly new to Linux but have used and installed the previous Ubuntu build without hassle and used it for several months.

I've been trying to do a clean install on a dual boot system and having some trouble.

I used Partition Magic 8 and set up a Ext2 partition and a linux swap. Went ahead and downloaded the proper iso image, burned it, and booted up.

My first install process asked me dozens of questions about things I want to enable, information about my hardware, etc. I followed most of the advice given (such as when it comes to graphics cards, to disable the communication for auto detect if I have a NVidia card), and finished my install. When the system booted, the GUI failed to boot and I was given an extensive error message (which, regretably, I did not write down) and kicked into a command prompt. I've read some of the possible fixes I can download but it seemed most of those operated off the assumption that I was logged in, just having display issues, not being unable to load my GUI. During the install process, I did notice Ubuntu seemed to identify my card as it installed a package dealing with NVidia but alas, no GUI.

I've tried to rerun the install process a few times but every time I attempt to reinstall, it automates every process! It doesn't ask me about the custom setup features like the original installation process. I've used different floppy disks/formatted them (I install the GRUB loader onto a floppy), I've formatted the partitions and recreated them, and I still cannot get back the original setup process I went through.

Any tips to either get the GUI working properly or to reclaim the original install process so I may attempt to select a different command to acurately work with my graphics card? My card is a BFG FX 5500 OC and when I used 5.04build, I was using an onboard card, which I have disabled in my BIOS since getting this new card, which is PCI slot.

---

### Post by sfdxsm on 2006-02-05
ive just also attempted to install a network install from a minimal cd from debian.org and was given all the options about my install process. this time around i allowed the process to auto detect my card and monitor. it found everything just fine but once it tried to boot the gui (x server i believe it is) it said fatal error: no display detected. Open SuSe seemed to have similiar trouble.:confused:

---

