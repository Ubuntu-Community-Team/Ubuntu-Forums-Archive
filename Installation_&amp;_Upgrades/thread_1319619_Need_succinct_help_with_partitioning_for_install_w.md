---
title: "Need succinct help with partitioning for install with existing Windows"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by david.karr on 2009-11-08
I have Windows installed on a box.  I want to install 9.10 on this box so I can choose which one to boot at restart.  I'd like to partition the single disk so that more than half of the space is available for Ubuntu.

I'm a relatively experienced Unix user, and I've been running 8.10 on another box for a while.  That box is also running Windows, which I can choose at startup.  I don't remember what the installation choices looked like for that old box, but the instructions I get when installing 9.10 are definitely somewhat different.

I could make some guesses in the install, but when making partitioning decisions, I really don't want to guess.  I've looked through the existing documentation that I can find, and I really can't find anything that really makes it completely clear exactly what I need to do.  The instructions on the Ubuntu site aren't clear enough for what I would think is an extremely critical point of the installation.

So, on the "Prepare disk space" step, I have the choices of "Install them side by side, choosing between them each startup" and "Specify partitions manually (advanced)".  This page also seems to imply that the default partitioning will divide the disk in half.  I see that the little graphical area that shows how the disk will be divided has a movable divider, but I don't see anything that clearly states that whatever value I set it at will be used for the "Install them side by side" option.  When I tried moving forward with the "Specify partitions manually (advanced)" option, it replaced the simple partition map with all orange.  The next page seems to give me the ability to repartition, but it seems relatively complicated, and I don't see clear indications on that page for exactly what I need to do.

My drive is about 320gig.  My best guess, if I had to proceed without any confirmation, is that I should be able to move the slider so that about 90g is used for Windows, and the rest for Ubuntu, and then the "Install them side by side" choice will automatically repartition the drive that way and continue the install.  I can't proceed from this step unless I'm sure this is what it will do.

---

### Post by raymondh on 2009-11-09
> **david.karr said:**
> 

My drive is about 320gig.  My best guess, if I had to proceed without any confirmation, is that I should be able to move the slider so that about 90g is used for Windows, and the rest for Ubuntu, and then the "Install them side by side" choice will automatically repartition the drive that way and continue the install.  I can't proceed from this step unless I'm sure this is what it will do.

Yes ... moving the slider will set allocations in a side-by-side install. That is the same as when you installed Intrepid.  

Other option is to create the partitions beforehand and then 'manually' install unto them.

Whatever you decide, have a working back-up of your files first.  Also, try the liveCD of 9.10 and see if basic functions suit your needs and preferences (Fkeys, sound, wifi, etc).

Regards,

---

