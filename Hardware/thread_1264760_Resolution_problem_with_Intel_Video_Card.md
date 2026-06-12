---
title: "Resolution problem with Intel Video Card"
date: 2009-09-12
forum: Hardware
---

### Post by gwu777 on 2009-09-12
Hello everyone,

I have a samsung V25 Pentium 4 2.4gh with 512Mb memory. it has an Intel 845GV IGD onboard card.

I have been running ubuntu 7 and 8 with compiz previously. I am now trying to configure the graphics in 9.04.

I understand that there is some issue with the drivers of the above. Apparently jaunty is not as good as before to handle them. 

I am just trying for the moment to change my resolution to 1024 - I am not even thinking of running compiz! Unfortunatly when I go in the display manager, there is no option to view th current resolution or change it. The boxes are greyed out. I now I am on 800x600, but it doesn't even say it! There are no monitor detected. It is problematic.

I used to reconfigure 8.1 with gtk displayconfiguration. Now this is not available in 9.04, it is a real shame... As the automatic version doesn't seem to work.

I have tried to reverting the Jaunty Xorg intel driver to 2.4 following various forum, it hasn't helped my problem.

Many on the forums seemed to say that the only solution is to revert to 8.1. Honestly I would be very disapointed with that? I really hope that some of you will be able to help.

Thank you very much.

---

### Post by gwu777 on 2009-09-14
I hope it is OK to do a up...

---

### Post by gwu777 on 2009-09-16
Anyone?

---

### Post by noobie1 on 2009-09-20
Good to see someone else with a v25.  
Unfortunately I am also having trouble.  

I just installed 9.04 and the system test seems to say that its running 1024x768, even though there is nothing in the display settings.

It had trouble in the tty screens where the right side was a copy of the left.  This seemed to fix itself when I added a vga=792 to the kernel line in grub/menu.lst

However, I'm having trouble with the screen going off and can't come back on (and the above seems to have made it happen when switching to tty screens in addition to sleep mode/ occasional login before). I don't think compiz would install - I may be doing it wrong.

---

### Post by lswb on 2009-09-20
I have a Pentium M laptop with intel 855 graphics. I got good results by following instructions in [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582). I am using what that thread calls the "bleeding edge" method though it is not quite so bloody as when the thread was first written. I have added the xorg-edgers repository as explained in the thread and currently am using the 2.6.30.5 kernel packages from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/). The kernel packages have to be downloaded and installed with dpkg. 

Applying this fix can seem somewhat intimidating; If you can hold out another month or so 9.10 will be released and hopefully the intel problems will be sorted out.

---

### Post by gwu777 on 2010-02-18
I took drastic action, I bought a new laptop and ubuntu works fine, at last.... It has only been 4 years I was trying!!!! lol

---

