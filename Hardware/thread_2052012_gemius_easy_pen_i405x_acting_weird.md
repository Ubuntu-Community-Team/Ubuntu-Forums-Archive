---
title: "gemius easy pen i405x acting weird"
date: 2012-09-02
forum: Hardware
---

### Post by shababhsiddique on 2012-09-02
I have a inexpensive graphic tab gemius easy pen i405x which is in good condition. When i connect it to my ubuntu precise its detected (i believe) as i can move the cursor by moving the pen across the board, but i cant click by pushing the pen towards the pad. 

what do i have here?

When i go to wacoom graphics tablet from the system settings menu it shows no tablet detected. And one more weird thing is sometimes the touch "does something" like when i am browsing the net, the touch doesnt click instead it goes "back" as if I right clicked and pressed the back option. I am pretty sure something like this happens. 

But it doesnt do anything at all when I touch on some other application for example I am willing to work with it on inkscape, but there touching absolutely does nothing.

This is a very emergency problem Its kind of my job. Please someone help. I can give further information if anyone point me what to do.

---

### Post by Favux on 2012-09-02
Hi shababhsiddique,

First let's confirm what you have.  When you run **lsusb** in a terminal you should see in the tablet line:
```
0458:5010
```
That's the Vendor ID and Product ID.  Go ahead and post that line.

Support for that model tablet is not available until the 3.4 kernel and Precise has the 3.2 kernel.  See the DIGI*mend* project:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)

However Nick has made kernel patches so you can add support to the 3.2 kernel and also rolled some pre-patched kernel packages:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend)

For some Ubuntu specific info. and instructions for patching see [HOW TO Add Support for KYE, UC-logic, and Waltop Tablets in Ubuntu]("http://ubuntuforums.org/showthread.php?t=1946486").  Because of the forum policy change the HOW TO hasn't been updated to reflect the newer 3.2 kernels Nick has rolled.

---

