---
title: "Tricky Problems in Lucid Linux 10.04 beta2"
date: 2010-04-22
forum: Hardware
---

### Post by dartdog on 2010-04-22
I have been working for days on putting Lucid on a Gateway mx6028 laptop with a new hard drive,, But I'm beginning to understand that my problems.. may be more generalized.. but tricky

Basically the install can be done from The lucid install only if the disk has been wiped,, otherwise the grub or mbr is messed up (don't know which)

I take a backup using Remastersys <<< Bravo!! BEFORE updating anything to do with video drivers (see next paragraph)...( I just tested one made after the video updates and it would not load....)

Then I must apply the "bulk auto" updated in small batches leaving out anything to do with open GL,, Then apply open gl related updates last....Failing to do this and something gets messed up with the video drivers and the system will not restart. 

So after this I get a good install and I ran another backup (which does not work) Seems to have the same video hangup as if I bulk update...

So with my Good system with the video updates running I ran the bulk update script from [http://www.unixmen.com/linux-tutorials/956-things-to-do-after-a-fresh-install-of-ubuntu-1004-lts-lucid-lynx-made-easy-with-ubuntu-start-script](http://www.unixmen.com/linux-tutorials/956-things-to-do-after-a-fresh-install-of-ubuntu-1004-lts-lucid-lynx-made-easy-with-ubuntu-start-script)

All looks fine and I get a bunch of neat stuff.. one problem,, on reboot I'm back to No-restart due it seems to bad video.. I get different size on the startup Ubuntu screen followed by a flash that sort of seems like a bad resolution setting followed by black... and no disk,, so I go back to the pre video install that I made with Remastersys

So a) hope this helps someone.. 
b) hope someone can figure out what is wrong....

---

### Post by dartdog on 2010-04-22
Have found that there is a Known problem with older Intel Graphics,, in the release notes,, 10.04 ([http://www.ubuntu.com/getubuntu/releasenotes/1004](http://www.ubuntu.com/getubuntu/releasenotes/1004)) Two suggestions modify the Grub 2 boot loader and possibly try other default Intel "experimental" drivers...

I was trying to modify the grub file but it is marked read-only.. so not sure how to fix that,, (I am a newb) I was also looking at the "new driver" described sort of here [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) and..[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) 

but not sure how to get that either...
Got to break from this...
I just want a working system!! that does not blow up when I update it..

---

