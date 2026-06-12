---
title: "Ubuntu LTS server; &quot;No disk drive was detected&quot;"
date: 2009-10-13
forum: Installation &amp; Upgrades
---

### Post by Milamber_Cubed on 2009-10-13
Hi All,

I am trying to install ubuntu-8.04.3-server-amd64 on a new build machine without much luck. 

The hard drive being used is a standard SATA drive which has been yanked from a windows system. Amazingly enough if left to its own devices, the Windows install boots and can log in - despite complianing that the hardware has changed and a re-validation is required. 

The above Windows experience gives me confidence that the various settings in the BIOS have enabled all of the IDE emulation options that the SATA controller has which makes the problem I am having all the more confusing; the installer simply doesn't see any disk drives. 

If I remove the install CD and let the system boot, Windows starts as above. If I boot from the CD and choose "boot from first hard disk" then Windows also does it's thing without any problems. Only when I try and get into installing Ubuntu on to this drive do I have problems with anything.

I get a message telling me that "No disk drive was detected" and a list of potential drivers to choose from for controllers. I have tried a few that seem like they may be a decent fit but nothing has been successful so far.

Any help in this would be very much appreciated!

For reference, the MB is the Gigabyte eq45m-s2, which has an ICH10DO South Bridge chipset. I haven't been able to find anything relating to this that is of any help.

---

