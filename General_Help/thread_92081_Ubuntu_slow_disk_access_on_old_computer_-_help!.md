---
title: "Ubuntu slow disk access on old computer - help!"
date: 2005-11-18
forum: General Help
---

### Post by ahallubuntu on 2005-11-18
I've inherited an older computer, a Celeron 466MHZ, that is a little slow on the latest Ubuntu BB.  What I mean is, it takes about 20 seconds to start up an Open Office window.  Other apps like Firefox take a bit longer than I'd like to start up.  I upgraded the machine to 256MB before the install so that should not be the issue.  The hard drive is a fairly old 4GB - probably ATA/33 - but it has plenty of space left after the install.

I've had Windows 2000 on this same machine and it runs much faster (even if not blazing fast), is much more responsive than Ubuntu.  But it's not a legal copy of Windows (or rather, I'm already using the legal license and this machine is going to someone else).  I can only guess the Linux driver for my IDE card and/or the old hard drive aren't optimized for the hardware.

I also tried a distro called Ubuntu Lite that as yet I have not been able to install successfully, though I love the concept.
 
Any suggestions for speeding this up?  This is just the first computer of several of this vintage that I expect to inherit (for a non-profit group) and I had truly hoped get away with some memory upgrades at worst.  I know with old computers you kind of have to take what you get, but I was hoping to do better than this.  Thanks!

---

### Post by aysiu on 2005-11-18
Enable extra repositories (first link in my sig).
Then type this in a terminal ```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```
Log out.
Click "Session"
Select "XFCE"
Log in.

---

### Post by willdeb on 2005-11-18
For faster disk access, you can try hdparm. But be carefull with it, it can damage your hard drive!

---

### Post by ahallubuntu on 2005-11-18
Thanks to both of you.  I made an image of my initial Ubuntu install so I'm willing to experiment with the one I have, if I screw it up I can always just restore the image.

---

