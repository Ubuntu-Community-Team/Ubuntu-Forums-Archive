---
title: "IBM Thinkpad T21 does not automatically load X"
date: 2008-01-18
forum: Hardware &amp; Laptops
---

### Post by MrE on 2008-01-18
Hi,

I've just installed Kubuntu Gutsy on two Thinkpad T21 laptops, using the alternate install CD as the Live CD would crash upon loading the desktop.

Both laptops won't automatically start X and boot in text mode only. After logging in, X loads fine using startx.

I can't seem to find anywhere how to get X to start automatically.

Can anyone point me in the right direction?

Also, both laptops have the same video card, a S3 86C270-294 Savage IX-MV using the savage driver. however on one laptop everything works fine whereas on the other one I just get a black screen when loading X.

I can only get X to load correctly on this second laptop using the vesa driver.

Any ideas?

Thanks
Emile

---

### Post by MrE on 2008-02-05
I'd really appreciate some help on the X not starting automatically issue.

Is there anyone out there who could possibly shed a light on why both my IBM Thinkpad T21 laptops refuse to load X on bootup?
To clarify, both machines were installed using the Gutsy alternate install CD and both ended up not loading X.

I can't find any errors in the various log files, and X starts quite happily if I type startx after logging in - it just won't start automatically.

[LIST]
[*]/etc/X11/default-display-manager is set to /usr/bin/kdm
[*]the file S13kdm is present in /etc/rc2.d, /etc/rc3.d, /etc/rc4.d and /etc/rc5.d
[/LIST]

Is there anywhere else I could look?


---


As for the second problem, the laptop that would only work when using the vesa driver, now works fine using the savage driver after adding

```
Option   "BusType" "PCI"
```

to the Device section in xorg.conf

I hope this helps someone else with a T21 and savage driver problems

---

### Post by Yellow Pasque on 2008-02-05
When you get stuck in the "black hole", press Ctrl+Alt+F1 and look at /var/log/Xorg.0.log
```
vim /var/log/Xorg.0.log
```
See if that gives you any clues as to why X doesn't load.

---

### Post by MrE on 2008-02-05
Hi,

Thanks for your reply.

Unfortunately I can't find anything meaningful in the log file you suggested.

The problem is that X works fine if I launch it using startx. It loads kdm and the desktop without problems and I can use everything just fine.

I am stuck on the fact that X won't start automatically, like it does on my desktop PC and my Toshiba laptop. I'm sure it's got something to do with the runlevel, but I don't know where to look. The startup script for kdm seem to be in place and the default display manager is correctly set to kdm.

The strange thing is that both laptops, both T21 models, exhibit the same behaviour.

---

