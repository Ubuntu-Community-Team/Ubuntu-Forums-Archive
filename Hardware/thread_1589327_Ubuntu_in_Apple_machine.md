---
title: "Ubuntu in Apple machine"
date: 2010-10-06
forum: Hardware
---

### Post by JCM_Pico on 2010-10-06
Hi there,
I'm about to change my old laptop for a new one. I've been searching for laptops and found the Apple machines very appealing. However, I need linux to work and therefore need to know how it behaves on Apple laptops.
Is there any incompatibility between those machines and the Ubuntu system?

---

### Post by srs5694 on 2010-10-06
You may want to check the [Apple Users](http://ubuntuforums.org/forumdisplay.php?f=328) subforum here. AFAIK, Ubuntu will install and work on most or all modern Apple computers, but I don't know offhand if every piece of hardware (built-in Webcames, Wi-Fi, etc.) is supported. Partitioning and booting can be a nuisance; most of the tutorials seem to treat Linux like Windows, creating an ugly and dangerous [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) configuration -- and there seems to be a bug in recent versions of some utility that do this incorrectly in at least some cases, requiring manual adjustment with fdisk to fix. (I seem to be answering one or two cries for help on this topic each week.) Unfortunately, I don't have a recent Intel-based Mac to test with, but there must be a way to do the installation *without* creating that hideous hybrid MBR -- at least unless you also want to boot Windows. (AFAIK, the hybrid MBR is required to boot Windows on a Mac.)

One issue you may run into is that Apple still insists on shipping single-button mice (or track pads, for laptops). Linux's GUI assumes three mouse buttons. There's a workaround for this that involves keyboard keys. If you can live with that, it shouldn't be a big deal. If not, plan on using a separate plug-in mouse or trackball with your laptop.

---

### Post by Terc on 2010-10-06
> **srs5694 said:**
> You may want to check the [Apple Users](http://ubuntuforums.org/forumdisplay.php?f=328) subforum here. AFAIK, Ubuntu will install and work on most or all modern Apple computers, but I don't know offhand if every piece of hardware (built-in Webcames, Wi-Fi, etc.) is supported. Partitioning and booting can be a nuisance; most of the tutorials seem to treat Linux like Windows, creating an ugly and dangerous [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) configuration -- and there seems to be a bug in recent versions of some utility that do this incorrectly in at least some cases, requiring manual adjustment with fdisk to fix. (I seem to be answering one or two cries for help on this topic each week.) Unfortunately, I don't have a recent Intel-based Mac to test with, but there must be a way to do the installation *without* creating that hideous hybrid MBR -- at least unless you also want to boot Windows. (AFAIK, the hybrid MBR is required to boot Windows on a Mac.)

One issue you may run into is that Apple still insists on shipping single-button mice (or track pads, for laptops). Linux's GUI assumes three mouse buttons. There's a workaround for this that involves keyboard keys. If you can live with that, it shouldn't be a big deal. If not, plan on using a separate plug-in mouse or trackball with your laptop.

For _years_ Apple has been shipping mice with multiple buttons (mighty mouse was sides, right, left, center, scroll up/down, scroll left/right).  The new "magic" mouse is one click, but simulates right/left/center by detecting how many fingers you use to click.  Scroll works using two fingers to slide (a feature ubuntu supports on my old acer laptop).

All glass trackpads use a similar scheme to the magic mouse - 1 finger is left, 2 fingers is a right click, and three is a center click.  Scroll works left/right up/down using two and they also have software based gestures.  I can't say how much of this works on Linux since I prefer vertical mice - even when on the go, but I'm tired of seeing the misconception that Apple mice only support left click.

---

### Post by JCM_Pico on 2010-10-06
well, the hardware compatibility problem with wi-fi and web cam I'll  have any way when buying a PC, and those fixes to dual boot seem quite  similar to the ones with windows dual booting, and has Terc said nowadays the mouse is like a 3 button mouse... So in the end I confused to what laptop would fit me better.

---

