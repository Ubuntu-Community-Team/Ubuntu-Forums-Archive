---
title: "Best Way to Upgrade Video Card?"
date: 2010-05-10
forum: Hardware
---

### Post by mattlach on 2010-05-10
Hey all,

I will be upgrading from a Geforce 9400 GT to a Radeon 5750 (fastest passively cooled board I could find) this week.   What is the best way of doing this?

I would imagine before swapping out the board, I should remove the nvidia proprietary driver?

For Radeon 5xxx series boards, what gives the best compiz performance right now?   FGLX or open source drivers?  I don't really care about 3D performance (I ahve Windows for that). I just want a useable desktop experience.

I have alsu heard of some 5xxx problems per this bug:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/560306](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/560306)

If it is caused by the opensource kernel driver, maybe it would make sense to install FGLRX before even installing the board?

Any help appreciated.

---

### Post by mattlach on 2010-05-11
Well,

I'll be receiving my card today, so I'll try the method above and report on how it works, I guess :p

---

### Post by mattlach on 2010-05-12
OK,

I ununstalled the Nvidia closed source drivers and control panel, shut down the computer, installed the Radeon 5750 and booted back up.

The Open source drivers appear to work without any further finageling with the following exception.

I got a dialog about X going into "limited graphics mode" or something to that effect.  After booting up fully it was apparent that I no longer had any Glitz/compiz effects.  I gather this is because the open source GL drivers don't fully support this yet for Evergreen based boards.

I may try using FGLX soon, but I have heard that they can be comparatively buggy.  We'll see.

Is there a way to get the latest X drivers mentioned [here](http://www.x.org/wiki/RadeonFeature)?

According to the program support page these seem to have more functionality in them than even the ones that come with Lucid.  Is there maybe just a kernel module I can get form somewhere and replace what's currently installed?

---

### Post by dino99 on 2010-05-12
fglrx is not the best and there are lot of issues, better to add this ppa on your repo:

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

you will have the latest driver

this one can be usefull too:

[https://launchpad.net/~ricotz/+archive/unstable](https://launchpad.net/~ricotz/+archive/unstable)

---

### Post by mattlach on 2010-05-12
> **dino99 said:**
> fglrx is not the best and there are lot of issues, better to add this ppa on your repo:

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

you will have the latest driver

this one can be usefull too:

[https://launchpad.net/~ricotz/+archive/unstable](https://launchpad.net/~ricotz/+archive/unstable)

Excellent!  Thank you.

Is there a way I can limit this to just installing mesa, and getting everything else from the stable Ubuntu repos?

I don't want to add these repos and find that my system wants to mass update to lots of potentially unstable packages...

---

### Post by mattlach on 2010-05-12
I just found this that looks promising:

[https://launchpad.net/~xorg-edgers/+archive/drivers-only](https://launchpad.net/~xorg-edgers/+archive/drivers-only)

---

### Post by mattlach on 2010-05-13
Hmm,

I did add this to my sources, and it downloaded a newer GIT compile of the ATI driver, and even with it added, my video card would only use software renderding, and thus Compiz would not work.

This is surprising since the "Program Feature" section on the X11wiki suggests that Compiz has "Gold" functionality with Mesa 7.7...

My best guess is that for some reason the module is not running, but I can't figure out why.

I tried mentioning the "radeon" module manually in xorg.conf but this didn't work.  I even tried "modprobe radeon" followed by a restart of GDM with no success, though an lsmod showed that the module was infact inserted and running...

Do you have any suggestions?

I tried installing FGLX,  and you are right, even the latest version has some serious bugs, including open gl 3D screen savers not clearing when shut down and the dialog box asks for a password.  I'd much rather go back to the open source driver if I can get it working.

Any help appreciated!

---

