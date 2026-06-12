---
title: "Black Screen after driver upgrade...Newbie"
date: 2008-10-11
forum: General Help
---

### Post by eccosam on 2008-10-11
Hi, I'm having a problem here with Black screen (no video) after everything was working great with this new install and decided to use sypatic update for the "New" Nvidia driver...Ubuntu.

I'm a newbie to Linux and loving it so far, just at a loss as to how to get back in:)

I installed the prog called Mythbuntu 8.04.1 and all was well with the driver it come with, but did not fit my monitor so that's why I decided to upgrade to this driver:confused:

I have been reading and tried Ctrl+Alt +F1 at bootup but nothing happens.

I have a screen comes up at boot that gives me a choice of 5 things. One of theme is a (recovery mode) but not sure what to do here

I could reformat and re-install again, but would like to figure this out. Mythbutu splash screen comes up, it loads then goes to black screen. At this point Ctrl+Alt +F1 does nothing:lolflag:

My system :

Asus P5Q-E with P45 intel Chipset
     Nvidia 9600 GT video card
     4 gig ram
     500 gig sata Linux Kernel 26.24.19 generic
     160 gig sata

Thanks for any help

---

### Post by linux_lover69 on 2008-10-11
Go into recovery mode and once its loaded click on repair x server.

---

### Post by eccosam on 2008-10-11
> **linux_lover69 said:**
> Go into recovery mode and once its loaded click on repair x server.


Hi, but still not sure how to get into recovery mode... I have these choices when I reboot:

-Ubuntu 8.04.1, kernel 2.6.24-19-generic

-Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)

-         "     MeMTest 86+

-Other operating systems

-Windows Vista

When I go to the second choice Recovery mode it lists all my devices by the looks of things, but not sure...if I type:

sudo dpkg-reconfigure xserver-xorg, it takes a minute or so and says...Done amd goes Dropping to a shell!

Buisybox

(initramsfs)

By this quote "once its loaded click on repair x server" I'm not sure if I'm in the right area to do this. Is there another way to get into recovery mode? Or what could I be doing wrong???:lolflag:

Again, when I use the first choice, Mythbuntu boots up...loads the splash page, then screen goes black. If I use Ctrl+Alt+F1 nothing happens there also...Mmmmm interesting

---

### Post by linux_lover69 on 2008-10-22
Sorry the click repair x server is in my ubuntu, im not sure about mythbuntu. But i'll look it up

---

