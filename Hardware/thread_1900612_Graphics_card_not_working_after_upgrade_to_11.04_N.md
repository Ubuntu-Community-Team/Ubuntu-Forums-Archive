---
title: "Graphics card not working after upgrade to 11.04 Natty Narwhal"
date: 2011-12-26
forum: Hardware
---

### Post by knasil on 2011-12-26
Hi all, 

Until yesterday I had a very happy computer running on Ubuntu 10.10. My problems started when I upgraded to 11.04 Natty from a CD. Natty would crash after a few lines of the installation screen. I removed one by one the hardware components until I found the culprit: the graphics card (ATI Technologies Inc RV515 [Radeon X1300] sitting on a PCI express slot). I switched the BIOS system to the built-in graphics card (Intel Corporation 82915G/GV/910GL Integrated Graphics Controller) and the installation proceeded OK.

Since I really like my (more expensive) Radeon X1300 I started to see whether I could use it or not... Mind you... It was working perfectly happy before!!!

I did try the common recommendations: removing Catalyst/fglrx, downloading and reinstalling the latest Catalyst package, ATI drivers, etc. (both cards are meant to be fully supported by the drivers). Since the computer only works under the Intel card, Catalyst does not run at all. Everytime I switch the BIOS to test whether I can run the ATI card, my computer crashes. I can only use the Intel card. 

May be for the same reason when I try "Systems==> Administration==> Additional Drivers" I see an empty box and the message "No proprietary drivers are in use in this system"

There is also the possibility that Ubuntu is trying to use the wrong graphics card: may be the BIOS is telling it to use the ATI card but Ubuntu is set up to use the Intel card. Is there any way that I can force Ubuntu to to use the ATI card? I cannot find the /etc/X11/xorg.conf file or anything that looks like it. What happened to this file (it was messy but handy to set up!)

My PC is a DELL running a 3GHz Intel Pentium 4 CPU with a Linux 2.6.38-13 generic kernel and 2Gb of RAM.

Since everything was working before, I am really considering to go back to Ubuntu 10.10! (aren't we supposed to keep improving from version to version?)

I hope you already know the answer to this.

best regards.

---

