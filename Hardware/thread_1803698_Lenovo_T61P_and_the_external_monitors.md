---
title: "Lenovo T61P and the external monitors"
date: 2011-07-13
forum: Hardware
---

### Post by ghstwrtr on 2011-07-13
I am running Kubuntu 11.04 on my T61P.  At one point (can't remember now what version I was on) I was able to use Fn+F7 to mirror my display onto a VGA monitor.  Alternatively, if I closed the laptop lid and re-opened it with a VGA monitor plugged in, it would also mirror my display.

Neither of these work anymore.  I understand that extending the display on the fly, Mac-style, is more difficult to do, but I would at the very least line to be able to mirror the display on the fly if needed.  Any advice is appreciated.

---

### Post by ghstwrtr on 2011-07-20
Here's a clue of some sort, I was reading up elsewhere and found mentions of the RandR extentions.  

 #> xrandr 
 RandR extension missing 

But if I look at the Xorg logs I find this:

 [    49.480] (II) Initializing built-in extension RANDR
 [    49.480] (==) RandR enabled

No errors showing.

I also noticed that on my Lenovo S12, if I plug in an external display, the KDE daemon picks it up and gives me a configuration dialog.  Not sure what I need to do on the thinkpad to get this to happen.

---

