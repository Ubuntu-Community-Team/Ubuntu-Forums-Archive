---
title: "Vsync out of control on tv"
date: 2009-08-23
forum: Hardware
---

### Post by theregoesmyeye on 2009-08-23
I don't really know if it's called vsync anymore on televisions, but if so it is completely out of control. The television picture is scrolling from up to down and flickers off and on randomly. Here is what i'm using:

lspci | grep VGA:
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon X1650 Pro (rev 9e)

FGLRX drivers 8.6 installed by Envy

S-video out to an older RCA television

Ubuntu 8.04 Hardy Herron

---

### Post by theregoesmyeye on 2009-08-23
Linux makes me look like an idiot once again. Score Linux!:KS

From within the Catalyst Controller, I set the television to M/NTSC and pushed CTRL-ALT-BACKsp  and now it works fine. Restarted it and it popped right back up.

---

### Post by theregoesmyeye on 2009-08-23
Well I ended up having to restart my computer, and now the silly thing is back to what it used to be, and doing what I previously mentioned doesn't help anymore.

---

### Post by theregoesmyeye on 2009-08-23
With me and my quick thinking I found a problem. For some reason the ATI driver wants to keep setting my tv format back to PAL-B. So I added a line in the xorg.conf under the "Device" section that looks like this:
```
Option        "TVFormat" "NTSC-M"
```
Pressed CTRL-ALT-BACKsp Waited for X to restart, the pressed CTRL-F1 then CTRL-F7 and it works again. I don't understand the CTRL-F1 and CTRL-F7 thing, but whatever the reason, it works. It looks like movie night is resumed again!:popcorn:

If this has helped you please leave a comment.

---

