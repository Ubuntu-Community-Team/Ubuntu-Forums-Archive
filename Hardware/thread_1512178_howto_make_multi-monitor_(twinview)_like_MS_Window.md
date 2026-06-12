---
title: "howto make multi-monitor (twinview) like MS Windows"
date: 2010-06-17
forum: Hardware
---

### Post by roop_s on 2010-06-17
i setup multi-monitor (nvidia twinview) without issues on 10.04. The behavior is somewhat different than what i'm used to on windows:

1) if i put a window on the second monitor and maximize it, it expands and fills both monitors. I expect it to fill only the screen this window is in

2) all new programs and dialog boxes open in what would be the middle of the two screens. this causes the new windows to appear half on one monitor, half on the other. i would expect new windows to open in the primary monitor or at least on their last used monitor.

has anyone been able to make multi-monitor more like MS windows which i'm more used to?

---

### Post by steveneddy on 2010-06-17
I believe the easiest way to set the root screen is to:

1. See if there are settings for this in **nvidia-settings**

2. install **grandr** and see if there you can set the root window

```
sudo apt-get install grandr
```

---

### Post by roop_s on 2010-06-17
sigh... 

ubuntu had ~180 updates to do including a new kernel so i let that go through and rebooted.

on reboot both #1 and #2 are no longer occuring!

if i maximize a window, it maximizes only to the screen it's on

when a new dialog or window opens, it opens on the primary monitor.

if i knew why the behavior changed that'd be nice but i think i'll sleep ok without it.

---

### Post by steveneddy on 2010-06-17
> **roop_s said:**
> sigh... 

ubuntu had ~180 updates to do including a new kernel so i let that go through and rebooted.

on reboot both #1 and #2 are no longer occuring!

if i maximize a window, it maximizes only to the screen it's on

when a new dialog or window opens, it opens on the primary monitor.

if i knew why the behavior changed that'd be nice but i think i'll sleep ok without it.

Sweet! Mark the thread as solved and we're done!

---

