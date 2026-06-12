---
title: "Asus n10j-a2"
date: 2009-03-05
forum: Hardware
---

### Post by Angelus1818 on 2009-03-05
Hello all,

I firstly want to say I am very happy to have found Ubuntu Studio. I've always loved Ubuntu but the fact that a lower latency kernel is available with almost all the software I need upon install, it's heavenly. 

So I got myself an ASUS N10J-A2. Ironically, not so much for the gaming. I wanted the moist powerful netbook available, I believe this happens to be it. I wanted something ultra portable that I could do all my art work and multimedia on. When I found "LMMS" (A freeware alternative to FL Studio, which I use on my desktop) I was ecstatic. So I made a bootable USB Drive of Studio 8.10 and installed it. However a lot of my hardware is Not working...

The main thing I noticed is that no form of internet works. Not wireless or Ethernet. I need a form of connection to use the download manager and to activate my nVidia card etc. Any help you guys may be able to pass on would be very grateful. 

Thanks, I look forward to hearing your responses.

EDIT:

I apologize!!! 

I will search the forum next time I need help before posting. If you knew what was up in my world right now you would understand me being a doof, but I think I got it now. I need to upgrade the kernel I believe....I found a tutorial for the A1 on this forum...sorry guys....

---

### Post by hotweiss on 2009-03-05
This should answer any questions that you might have:

[http://forum.notebookreview.com/showthread.php?t=315810](http://forum.notebookreview.com/showthread.php?t=315810)

---

### Post by avilella on 2009-04-05
If you have access to a ASUS N10J and have tried to run Linux, please take a moment to provide the DSDT information for the laptop in this link:

[https://bugs.launchpad.net/bugs/312756](https://bugs.launchpad.net/bugs/312756)

DSDT is an acronym for Differentiated System Description Table. This table contains the Differentiated Definition Block, which supplies the information and configuration information about the base system. It is always inserted into the ACPI Namespace by the OS at boot time.

If you've got a laptop with a IGP and a hybrid Nvidia or ATi card, and you have tried to use Linux on it, you may have noticed that there are issues with the hybrid graphics setup. To help improve the Linux hybrid graphics support for this laptop, please attach your DSDT information to this Launchpad bug report specifying your laptop model:

[https://bugs.launchpad.net/bugs/312756](https://bugs.launchpad.net/bugs/312756)

To compile your DSDT information, install if you haven't already the acpidump and iasl tools:
sudo apt-get install acpidump iasl           # on Debian-based systems

Then run the following commands:

sudo acpidump > acpidump.txt
sudo acpixtract acpidump.txt
iasl -d DSDT.dat

This will create a DSDT.dsl file that you can attach to the bug report. This information will allow the developers to fully implement the hybrid graphics features for Linux.

---

