---
title: "Xserver crashing NMI error - T60 laptop"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by IndigoMontoya on 2007-02-02
I am having a strange problem with my laptop.  I have found that when I leave my laptop on for a  period (and leave - it never happens when I am around - of course) my xserver seems to crash (it is at the login screen.  I am running an up-to-date edgy with beryl on an ibm T60 with an ATI video card.  One time it occurred I had another virtual terminal open and I received the error message:

```
Uhhuh. NMI received. Dazed and confused, but trying to continue
You probably have a hardware problem with your RAM chips

```

With some numbers associated (I copied the exact message from the web).  I have since run memtest86+ and had over 80 passes with no errors.  Also, this computer is an XP dual boot.  I rarely use it, but have never had a problem when in windows.  For no good reason I feel the problem may be with the fglrx driver.  Any thoughts?  Please.....

---

### Post by catfishk on 2007-08-19
take a look here: [http://www.math.sunysb.edu/~comech/tools/CheapBox.html](http://www.math.sunysb.edu/~comech/tools/CheapBox.html)

 this guy fixed his by:

 "changed the memory setting from 100MHz ("PC100 memory") to 66MHz ("non-PC100 memory"), which you can do with jumpers on MVP3-based Super-7 motherboard, and this healed the problem completely"

 obviously, we don't have the same hardware.  maybe our T60s were built with messed up RAM?  i have had these errors on three installs on my type 2613-HCU. i would really like to get my stuff replaced under warranty, while i have it, if is it a hardware issue

---

### Post by IndigoMontoya on 2007-08-19
I don't feel the problem is hardware related because it works fine in XP and memtest didn't have any issues.  In the past few months (with Feisty I bet) I have seen it less often, but still sometimes.

---

