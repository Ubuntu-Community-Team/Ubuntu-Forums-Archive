---
title: "Radeon HD 4850 has artifacts in bottom right corner"
date: 2009-07-20
forum: Hardware
---

### Post by Robotoer on 2009-07-20
I recently bought a Radeon HD 4850 for my computer that currently dual boots windows 7 and ubuntu 9.04.  Before buying this card, I used a geforce 7200GS.  Before replacing the card, all compiz effects (such as alpha bluring) worked perfectly, albeit laggily.  After replacing the card however, the computer complained about having an incorrectly configured X server graphical session.

Not wanting to try to fix problems without a clean system to start out with, I reinstalled Ubuntu and began to try to get it to play nice with my new ATI card.  As soon as I installed the proprietary ATI drivers from the hardware drivers manager, 3D effects worked again, with the exception of alpha blending (aka the Blur Plugin).  Unfortunately, the ATI drivers also caused there to appear some black and green artifacts in the bottom right hand corner of the screen.  The artifacts occupy roughly a 1 inch by 1 inch square in this corner and do not entirely cover the area, but are spread out throughout the region.  The artifacts' shapes and colors do not change from what I can tell.  The artifacts appear after the system has booted.  When I move the mouse over the artifacts, the artifacts are hidden behind the mouse cursor.

I have tried installing the latest ATI drivers and the artifacts are still there.  When the ATI drivers are uninstalled, the artifacts disappear.

Any help would be much appreciated, I don't want to have unusable pixels after just buying a new videocard.

Thanks.

---

### Post by komputes on 2009-07-20
A few things I would recommend:

Does alpha transparency blending work with this card on ubuntu 8.10 or 9.10? Check if the previous or next release which has an older and newer driver as well as an older and newer version of Xorg, you will be able to troubleshoot if there is a release which works.

Have you reported the issue to ATI? This would be halpful if they have a bug or regression to their driver.

Can you report a bug on bugs.launchpad.net and take a picture of these artifacts? Be sure to attach /var/log/Xorg.0.log to the bug.

---

### Post by Interpreter on 2009-07-20
Current proprietary ati drivers for that card are fubar for now. Guess we'll have to live with it until both the ubuntu guys and ati fix that. Deactivate 'em and that behaviour will go away. Yes that means no shiny desktop, but ATI "fu**ed up" with their recent release and the Ubuntu guys didn't double check enough. Google that cards name and the keyword linux. Major carnage all over the real world and the internet.

See here
[http://ubuntuforums.org/showthread.php?t=1188313]("http://ubuntuforums.org/showthread.php?t=1188313")

---

