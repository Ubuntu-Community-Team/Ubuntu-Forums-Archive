---
title: "I killed my ubuntu box"
date: 2008-09-27
forum: General Help
---

### Post by Atomsmasher on 2008-09-27
Hi all, I'm looking for some quick help on getting my ubuntu desktop back.  Here's the situation:

I am running ubuntu desktop 6.06 and the other day I wanted to grab the latest stuff for xine, like the xine-ui package.  So I went into Synaptic and chose the stuff that looked like it had to do with xine.  I did notice that it was removing some packages that might be important (starting with "lib*"), but I figured the package manager knew what it was doing.  I guess not.

After the machine downloaded the packages, installed and rebooted, I was stuck at the command line.  I tried running startx, but it said it couldn't connect to the X server.  After looking through these boards, I didn't see anything quite like this.

Any suggestions are welcome.  Thanks!

---

### Post by cariboo on 2008-09-27
Have you tried from the command prompt:

```
sudo apt-get reinstall ubuntu-desktop
```

This should restore your desktop.

Jim

---

