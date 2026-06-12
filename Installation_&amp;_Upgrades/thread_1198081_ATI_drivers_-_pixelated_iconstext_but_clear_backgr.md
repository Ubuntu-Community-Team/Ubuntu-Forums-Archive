---
title: "ATI drivers - pixelated icons/text but clear background and 3D"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by bleeper4 on 2009-06-27
hey all,

I haven't installed linux since the early days of Redhat...needless to say I'm impressed with how far distros have come since then.  I installed Ubuntu Hardy because I have an ATI Radeon 9600 (more 3D support from what I read), but I didn't get Half-Life 2 or CS:S working properly.  I tried to reinstall the ATI drivers (at the time they were the proprietary drivers installed via "Hardware Drivers" in Ubuntu system administration), but then my video just sank.

I've tried to install both the open source and the proprietary drivers in any way possible (installing automatically via apt-get, installing manually with ATI's .run, installing through Synaptic, etc), but the farthest I get is a weird screen where some things are fine and some things are pixelated-looking.  I've uploaded a screenie here:

[IMG]http://filebox.vt.edu/users/dengy/Screenshot.png[/IMG]
(the blue on the top is not what it looks like, I think that came from the screenshot)

As you can see, the background is clear, the mouse is fine, but all the icons and text, as well as menus, are funny-looking.  The menus shift to the right (and distorts that portion of the screen when I hover over them, and icons shift to become a part of the background when I hover over them.  Also, 3D runs fast and smooth, as you can see from Xmoto.

I know there is just one thing wrong with the drivers that can be fixed; it's simple enough to reinstall Ubuntu but I'd rather try and save all my installations.  Thanks for your help!

---

### Post by Mark Phelps on 2009-06-27
Unless your video card is one of the newer "HD" cards, all you've done by trying to install the restricted drivers is hose up your machine.  We've been posting regularly on this board for weeks about how AMD/ATI has dropped support for the older non-HD cards/chips and there are no restricted drivers that will work with those under Ubuntu 9.04.  If you weren't automatically offered restricted drivers, that's why.

So, what's the model of your ATI card/chipset?

---

### Post by bleeper4 on 2009-06-28
As I stated above, I have a Radeon 9600, XT.  I assumed that installing Ubuntu Hardy (version 8.04) I would have better support for the card.  Any help on it, or should I just reinstall?  Thanks.

---

