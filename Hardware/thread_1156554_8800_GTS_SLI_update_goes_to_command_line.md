---
title: "8800 GTS SLI update goes to command line"
date: 2009-05-11
forum: Hardware
---

### Post by Toast2120 on 2009-05-11
Didn't get a reply to this earlier, so here I go again.
My system is a 8800 GTS SLI, AMD 4200 (64bit), 4GB RAM

Now, on with the problems:
Just newly installed Jakalope. Looks fancy and new, got flash and sound to work, awesome. So naturally next are the drivers. Going to System -> Admin -> Hardware drivers I upgraded my video drivers (version 180.44-0ubuntu1). Restart. Here is what I got:

After the splash was finished the screen goes black to a command line. Text that appears:


kinit:  trying to resume from ......
kinit: No resume image, doing normal boot...
Ubuntu 9.04 tomato tty1

Tomato login:


After logging in the regular "Linux is free of charge" stuff comes up
and I can use my PC, though just command line.

Naturally I try "startx"

The cream of the crop seems to be
"Fatal server error:
no screens found"

So I'm pretty sure that's where my error stems from, but I have no idea how to fix this. For those interested in other code I have attached my "startx" error. I'm thinking my /etc/X11/xorg.conf is screwed up, but have no ideas how to fix it. Haven't tried taking out the SLI yet, get to that when I have the chance, though I don't think that's the issue.

---

### Post by Dark_Stang on 2009-05-11
You're probably having issues with the latest drivers just like I am.

Run
```
sudo dpkg-reconfigure xserver-xorg
```
To help you fix x.org. For now, just set it to use the vesa driver, which is a generic driver.
Then run startx.
Go system > administration > hardware drivers just like before, but select the older driver to install. The one I am running is 173. Then restart and see what happens.

---

