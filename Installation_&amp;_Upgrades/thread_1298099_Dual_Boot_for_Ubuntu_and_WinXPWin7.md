---
title: "Dual Boot for Ubuntu and WinXP/Win7"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by ltHank on 2009-10-22
I currently have a desktop that is running Ubuntu 8.10 64bit.  I'm looking to install Windows XP on it to dual boot with - however, the install of WindowsXP is only so I can use an upgrade install of Windows7 and save some cash (I've heard you can use the upgrade disk to make a clean install over XP and it is cheaper than buying a regular disk).

What is the best way to go about this?  I'm not averse to reinstalling Ubuntu either; I've heard you should install it second when doing these kinds of things, I'm just hoping there is a reasonable way to avoid that.

---

### Post by earthpigg on 2009-10-22
the easiest way (but not the 'most correct', some will say):

install windows, upgrade windows, get whatever you want to get done in windows done and final.

then run defrag a few times and go ahead and install ubuntu.

one thing you could consider, since you may be doing a fresh install anyways, is that ubuntu 9.10 is coming out around Halloween... maybe wait a few weeks so you can have the latest and greatest of both windows ***and*** ubuntu?


the 'most correct' way, some would say, is to leave ubuntu in place, go ahead and install/upgrade windows, then re-install GRUB afterwards. (windows installs and upgrades have a habit of eradicating anything kept in the Master Boot Record that is not from Microsoft, without asking the user, and replacing it with the Microsoft equivalent of GRUB - which will not easily recognize or work with Linux...)

reinstalling GRUB isn't difficult *per se*, but it does involve command line stuff. there are how-to guides and whatnot all over these forums and google.

---

### Post by ltHank on 2009-10-22
I do think I will wait until 9.10 comes out, actually, that's a good idea!  And thanks for the response, that's what I figured but I thought it best to check.  I'll probably look up how to reload the GRUB and see if that seems too tricky for me.  Wish me luck!

---

