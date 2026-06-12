---
title: "intrepid won't enable proprietary driver (ati)"
date: 2008-11-08
forum: General Help
---

### Post by Mzwo on 2008-11-08
hi,

just upgraded to 8.10 and encountered the following:

system=>admin=>hardwaredrivers does show the driver for my ati mobility radeon, but clicking activate won't actually activate it at all ... i can clikc activate as often as i can, it won't work.

also, fglrxinfo give me the following, which doesn't seem right

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  159 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10


something seems to be amiss, alas i don't kwno where to look. hints appreciated.

cheers,
Mzwo

---

### Post by Vipers on 2008-11-14
I too am having the exact same problem.

Can anyone help us out?

Thanks.

---

### Post by arpanaut on 2008-11-14
From the release notes:
[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

> ATI "fglrx" video support

The ATI video driver in 8.10 drops support for video cards with r300 based chips (the Radeon 9500 - X600 Series of cards). If you have such a card, please use "Hardware Drivers" at System/Administration to disable it before the upgrade. Please see bug 284408 for more information

---

### Post by Vipers on 2008-11-14
I have an ATi X1950 XTX so I'm not affected by the dropped support.  I did just notice Mzwo's running a mobility Radeon which I didn't see before I posted.


Also, on reboot, I get a message saying Ubuntu must run in low graphics mode.

---

### Post by Mzwo on 2008-11-14
as far as i'm aware, the mobility radeon hd 2400 shouldn't be affected. i went back to hardy but would quite like to upgrade again - anything steps i should be taking beforehand?

cheers,

Mzwo

---

