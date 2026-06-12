---
title: "Installing new RAM in 8.04  32-bit"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by AeroTITAN on 2008-12-29
I am trying to install 2, 1GB PC3200 184 pin memory in a 32-bit system.  They type (PC3200), the pin number (184), voltage, etc. are all compatible with my hardware.

I have recently (a week ago) updated to 8.04 LTS from 7.10.

So I installed the memory and booted up.  Ubuntu boots into a loop where it reaches the screen where the boot status shows you the progress, it will get to about a third of the way through and then reboots.  If it's relevant the computer beeps when it does this.

My system is dual boot with XP Service Pack 2.  Windows boots just fine.

Last week I also installed a new graphics card: Nvidia 8400 gs (PCI, not PCI-Express).  That was a pain to get working, where I actually had to update to 8.04 to get the graphics card to work.  Again Windows booted fine here too.  Eventually both XP and Ubuntu worked after that, but Ubuntu seemed to work slower after than (I must have to optimize that somehow).

So here's what I've tried:
1)  These commands:
sudo apt-get install linux-restricted-modules-server

sudo apt-get install linux-headers-server

sudo apt-get install linux-image-server linux-server

2)  Removed new memory and added old.  Ubuntu and Windows boots just fine which would make you  think the memory could be bad, except Windows boots just fine with the new Memory.

3)  Switched around placement of memory in different modules.  No joy there.  And again Windows boots fine.

4)  I was once to enter the Recovery Mode (although now it crashes) where I typed in the command: $ free
The output showed all of the memory including the new memory as present.

5)  The BIOS shows all the memory present.  I saw a post regarding an "optimization" setting and I don't have one.

6)  Currently trying to run the 8.04 32-Bit LiveCD.  It seems to freeze at the same place in the loading bar as the HDD.

I appreciate any help you can offer.

Thanks

---

### Post by overdrank on 2008-12-29
Please do not create multiple threads on the same issue. [Duplicate here]("http://ubuntuforums.org/showthread.php?t=1024469")

---

