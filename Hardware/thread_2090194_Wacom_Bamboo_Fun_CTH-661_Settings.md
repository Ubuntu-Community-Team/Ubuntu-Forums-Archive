---
title: "Wacom Bamboo Fun CTH-661 Settings"
date: 2012-12-01
forum: Hardware
---

### Post by MRFredB7 on 2012-12-01
Hi all,

I'm a new user currently running Quantal Quetzal on a Dell Latitude E6400. I own a Wacom Bamboo Fun Pen & Touch (CTH-661) Tablet. I am aware that Ubuntu comes with Wacom tablet functionality pre-installed and my tablet works fine with the exception of my ExpressKeys. They appear to not function at all when my tablet is connected and I've yet to figure out how to activate/map all 4 buttons.

I've read about and tried packages in repositories posted by other users for Ubuntu 10.04/10.10 but these don't seem to work in later versions of Ubuntu.

Anyone have any possible ways to get my tablet operating at full functionality?

Any help is much appreciated and I apologise if this issue has already been resolved in the past.

Cheers!

---

### Post by Favux on 2012-12-01
Hi MRFredB7,

Welcome to Ubuntu forums!


The Wacom tablet app. in System Settings doesn't support the BambooPT pad buttons yet because libwacom doesn't handle out of sequence keys from the kernel, which the BambooPTs have.  That's being worked on.

So you have to set them using xsetwacom commands, usually in a script.  See "IV. Use of a xsetwacom script file" and "V. Tablet (Pad) buttons" on the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  Also see one of the Linux Wacom Project's mediawiki pages:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)

---

### Post by MRFredB7 on 2012-12-01
> **Favux said:**
> Hi MRFredB7,

Welcome to Ubuntu forums!


The Wacom tablet app. in System Settings doesn't support the BambooPT pad buttons yet because libwacom doesn't handle out of sequence keys from the kernel, which the BambooPTs have.  That's being worked on.

So you have to set them using xsetwacom commands, usually in a script.  See "IV. Use of a xsetwacom script file" and "V. Tablet (Pad) buttons" on the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  Also see one of the Linux Wacom Project's mediawiki pages:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)
Hi Favux,

Shame there's no support for them yet but look forward to seeing it implemented.

Those links you've provided seem to be just what I was looking for so I'll give it a shot.

Thanks! :)

---

