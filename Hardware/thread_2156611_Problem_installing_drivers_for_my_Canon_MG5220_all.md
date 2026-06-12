---
title: "Problem installing drivers for my Canon MG5220 all-in-one printer"
date: 2013-06-22
forum: Hardware
---

### Post by Elaphe on 2013-06-22
Hello everyone!

I'm sorry if this has been asked and answered already, but I've searched and can't find a solution to my specific problem, and I'm getting very frustrated. I'm hoping someone here will be able to help me get my Canon MG 5220 all-in-one printer working. I have actually had this printer for a year or so, I found a great deal on it, and after a cursory search I discovered that many reported using this printer with Ubuntu, and I was reasonably confident that I too would be able to setup this printer without too much trouble. Unfortunately, in the year or so I've had it, trying off and on a few times, I've never been able to get this printer working with Ubuntu, and it's generally been an inconvenience. But now I really need to print something important, and it's suddenly become a priority to get this printer working, or it's headed for the recycling bin ;-) I would be greatly appreciative of anyone who can help me with this, or even just point me in the right direction.

Here's what I've done recently, and where I'm having a problem. As of last night I was running Ubuntu 12.04 (I think) on my 64 bit HP laptop. I searched and found a couple threads about installing the drivers for my Canon MG 5220, such as this one here:

[http://ubuntuforums.org/showthread.php?t=1475336](http://ubuntuforums.org/showthread.php?t=1475336)

In general, the information I found in the above linked thread, as well as others, suggested that I download Linux drivers for my printer from either the Asian or Australian Canon support page, unpacked them, and install the drivers. Well I tried that, and at first the install failed because of some architecture issues, I think it said. I followed the instructions to comment out appropriate portions of code in the install.sh file to force it to run on my 64 bit machine (see link above). Now, it goes past that part, but fails almost immediately complaining that "A necessary package could not be found in the proper location". It looks something like this:

me@Silverbird:~/Downloads/Drivers/cnijfilter-mg5200series-3.40-1-deb$ sudo ./install.sh
==================================================

Canon Inkjet Printer Driver Ver.3.40-1 for Linux
Copyright CANON INC. 2001-2010
All Rights Reserved.

==================================================
An error occurred. A necessary package could not be found in the proper location.
me@Silverbird:~/Downloads/Drivers/cnijfilter-mg5200series-3.40-1-deb$

This morning I did a fresh install of Ubuntu 13.04 64 bit, I tried the above steps, and again I get the same error. I have tried both sources of the driver, the one from the Asian site and the one from the Australian site with no luck. I have run the ./install.sh with sudo and without, and have tried to run the install from the command line as well as through Files (aka new Nautilus, right?). I have searched, but cannot find a solution to this specific error. In fact, it's just post after post of people that rave about how easy it was to get their printers going, if that isn't a kick in the pants, lol! So I must be doing something wrong, or I don't have something installed that I should, but I'm out of ideas. Could someome please help me figure out what I'm doing wrong?

Thank you in advance for your help!

-Elaphe

---

### Post by dino99 on 2013-06-22
[http://askubuntu.com/questions/168089/how-do-i-install-my-new-canon-mg5250-printer-mg5200-series](http://askubuntu.com/questions/168089/how-do-i-install-my-new-canon-mg5250-printer-mg5200-series)
[https://sites.google.com/site/mikescomputerstuff/ubuntucanonmg5220](https://sites.google.com/site/mikescomputerstuff/ubuntucanonmg5220)

---

### Post by Elaphe on 2013-06-22
> **dino99 said:**
> [http://askubuntu.com/questions/168089/how-do-i-install-my-new-canon-mg5250-printer-mg5200-series](http://askubuntu.com/questions/168089/how-do-i-install-my-new-canon-mg5250-printer-mg5200-series)
[https://sites.google.com/site/mikescomputerstuff/ubuntucanonmg5220](https://sites.google.com/site/mikescomputerstuff/ubuntucanonmg5220)

I don't believe it, but the steps in the first link worked perfectly for me! Thank you so much for your fast reply, I wish I would have asked a long time ago. Thanks again, dino99!

-Elaphe

---

