---
title: "Gutsy &gt; Acer 5100 problems w/ sound"
date: 2007-10-12
forum: Hardware &amp; Laptops
---

### Post by wastedfluid on 2007-10-12
Hi guys.

Just upgraded from 7.04...

KMix worked fine on 7.04,  the volume controls on my keyboard worked fine with no tuning.  Nothing..

However, after upgrading to 7.10..

When I turn the volume up with my laptop keys - it goes from 0% - to 11%, and then stops.  It's either 0, or 11%.  And it doesn't effect how loud the volume actually is.

alsamixer works, and even Kmix(if you open the control panel) controsl the volume PERFECTLY.

But it's something to do with ~/.kde/share/config/khotkeysrc'

Any ideas???

(khotkeysrc is way too large to paste..)

---

### Post by swisscow on 2007-10-12
Try right clicking the volume icon, select "select master channel" and choose master.

---

### Post by wastedfluid on 2007-10-12
I did.

Master is set to "PCM" - and it doesn't work.

If you press volume up - it goes to 11%.

If you press volume down, it goes to 0%.

IT goes no higher than 11%.. BUT, if you change the volume in kmix actually.. and drag PCM, it works.

Thanks for your reply!

---

### Post by swisscow on 2007-10-12
Ah sorry, can't help then. Reason I gave this answer was I has a sony laptop that did this and changing the master channel sorted it out. I've got an Acer now and the volume with gutsy works fine..............though that is sod all help to you!

---

### Post by wastedfluid on 2007-10-12
Ahh.. Thanks anyways.  Worth a try!!

Anyone else?

[http://paste.biz/paste-2851.html](http://paste.biz/paste-2851.html)

here is ~/.kde/share/config/khotkeysrc

I also added shortcuts in KMIx under "Global Shortcuts" for volume up + down, but still nothing.

Strange: the MUTE button works, though.

Here are results from xev when I press Volume Up + Down

```

FocusOut event, serial 31, synthetic NO, window 0x4000001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x4000001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   1   0   0   0   0   0   0   0   0   0

KeyRelease event, serial 31, synthetic NO, window 0x4000001,
    root 0x75, subw 0x0, time 2519946507, (651,434), root:(654,504),
    state 0x0, keycode 176 (keysym 0x1008ff13, XF86AudioRaiseVolume), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False

FocusOut event, serial 31, synthetic NO, window 0x4000001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x4000001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   64  0   0   0   0   0   0   0   0   0   0

KeyRelease event, serial 31, synthetic NO, window 0x4000001,
    root 0x75, subw 0x0, time 2519951245, (714,321), root:(717,391),
    state 0x0, keycode 174 (keysym 0x1008ff11, XF86AudioLowerVolume), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False

FocusOut event, serial 31, synthetic NO, window 0x4000001,
    mode NotifyNormal, detail NotifyNonlinear



```

I can confirm that using

```

dcop kmix Mixer0 increaseVolume 2
dcop kmix Mixer0 decreaseVolume 2

```

Any ideas?  It has to be something with khotkeys.  I'm going to have to switch hotkey managers if I can't figure it out.

---

