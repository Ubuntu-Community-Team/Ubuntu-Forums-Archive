---
title: "Synpatics touchpad going crazy."
date: 2007-05-21
forum: Hardware &amp; Laptops
---

### Post by wastedfluid on 2007-05-21
Okay guys.  Just installed 6*..

My synaptics touch pad is not working.  Just touching the touchpad to move my cursor, will drag/resize windows, highlight text, will paste if in a text box, and other just ANNOYING BEHAVIOR.. it's almost as if it treats the touchpad as a mouse and thinks with my finger touching it i'm clicking and holding.  Sensitivity, perhaps?  I went to System / Admin / -> Mouse, but that doesn't help.

I was told to install Gsynpatics.  I go to install gsynpatics, and I get this error message:

Error:  Dependency is not satisifiable: libatk1-0-0.

So I re-installed libatk in Synaptic Package Manager.  Still doesn't work.

Any suggestions?  I just want my touchpad to work.  This is driving me crazy.

---

### Post by snakedr on 2007-05-21
How did you install gsynaptics? If you are trying to compile gsynaptics it probably requires the libatk1.0-dev package.

Gsynaptics is available in the respositories. If you install it using *sudo apt-get install gsynaptics*
it will install any dependencies that are required.

---

### Post by smarchi on 2007-06-03
Hi

I'm having a problem similar problem with my synaptics Touch Pad. I use a Hp dv2035la laptop.
When I do a vertical movement, and near the buttom edge of the touch pad, the pointer does a "jump" towards down the screen. It seems that it only occurs whe dpoing a vertical movement.

Someone knows what the problem is?

Thank You

---

