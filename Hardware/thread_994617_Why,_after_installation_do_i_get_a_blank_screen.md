---
title: "Why, after installation do i get a blank screen?"
date: 2008-11-26
forum: Hardware
---

### Post by Noriyuke on 2008-11-26
Ok, i have a toshiba 1805-S203 and i tried installing zenwalk distro before being sent here and i had the same error on both, im an absolute noob to linux. so please, notify me as to what i can do to fix this to get xubuntu running on this system.

---

### Post by cariboo on 2008-11-27
Assuming you are running Intrepid (8.10), start in recovery mode and at the menu select xfix, let it finish and then select resume. This will get you in safe graphics mode and get to a desktop, where you should be able to install the resricted video drivers.

Go to System-->administration-->Hardware Drivers, choose the driver that is rescommended then click activate. This will take a while, so don't be impatient. The drivers have to be downloaded first then compiled for your kernel.

Jim

---

### Post by Noriyuke on 2008-11-27
Well the first paragraph or instructions were great until i hit resume, then the exact same thing happened.

---

### Post by Noriyuke on 2008-11-27
Sorry for bumping this up, but im kinda trying to get an answer.

The drivers for the video card can be located here:
[http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?selModel=1073833648|PS181U&modelFilter=1805-S203&rpn=PS181U&category=&selCategory=3&moid=1073833648&os=&ct=SB&selFamily=1073768663#contentArea]("http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?selModel=1073833648|PS181U&modelFilter=1805-S203&rpn=PS181U&category=&selCategory=3&moid=1073833648&os=&ct=SB&selFamily=1073768663#contentArea")

Its the Trident Cyberblade Ai1 that are needed, anyway to install those through recovery?

---

