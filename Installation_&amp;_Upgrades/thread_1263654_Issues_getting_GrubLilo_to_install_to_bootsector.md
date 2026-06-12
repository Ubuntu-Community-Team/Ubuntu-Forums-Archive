---
title: "Issues getting Grub/Lilo to install to bootsector"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by dragoryte on 2009-09-11
All,

I have searched through google and on this site and I can't seem to find the answer to this issue. I am going to be tri-booting my machine, for right now however I'm just worried about getting Windows 7 and Ubuntu 9.04 to play nice. I am using EasyBCD within Windows because I like the iReboot program that I can run in the taskbar to tell my system to auto-reboot into Jaunty or OSX once I get it installed. Here is the problem:

The drive I am installing on is actually 2 velociraptors striped. I have been able to get 9.04 installed with relative ease thanks to dmraid. Before I started loading anything I used the live cd, went into gparted and created the 4 partitions I wanted. 1 is NTFS for Windows, 2 is Ext3 for Ubuntu, 3 is Swap for Ubuntu, and the 4th is a Fat32 partition that I will later use to install OSX on-top of but like I said I am not worried about that right now. 

Windows was installed first, then I setup EasyBCD, rebooted and installed Jaunty on the 2nd partition. Due to dmraid (I'm guessing) I have found that I have to install from the secondary disc rather than the live CD, every time I try to use the live CD for installation it fails at around 95% of the install. So using the secondary disc I go through the manual install, point it to the correct partition for swap and install, get all the way through the install, get to the bootloader section and I run into an issue. I know that to get EasyBCD to work the way I want it to, I need to install Grub/Lilo on the boot sector rather than the MBR. The problem is, Grub only gives me the option to install on the MBR. Lilo doesn't directly say it will install on the bootsector but it does have an option to install it on the partition, when I try to use it, the window turns red and says this is impossible. I escape to the rest of the options and find 4 options pertaining to where I am right now. 1 Install Grub which only gives me MBR option. 2 Install Lilo which gives me both options but fails to install on the bootsector like I want. 3 No bootloader which I have trying to get EasyBCD to use NeoGrub with this option but it fails. 4 Finish installation essentially the same as option 3. 

Please help me get Grub/Lilo to play nice and just install on the bootsector. I don't want it on the MBR because like I said I like the options the EasyBCD gives with iReboot etc. Greatly appreciate any help in advance. 

PS I have tried SGCD, when I try to find the find /boot/grub/stage1, it comes back and says no data avail like it doesn't exist even when I have installed Grub. This is Ubuntu 9.04 64 bit btw.

---

### Post by ronparent on 2009-09-11
If that is what you want you would need to execute the setup command at the grub prompt as follows:

**setup (hd0,1)**

That work of course only if you have the grub program installed to /boot/grub (that is not clear from your narrative). If it is not there, I would have to give some thought to getting the software into the location without having setup run (which would of course write to the mbr).

---

