---
title: "Karmic 64 Hangs and Freezes on fresh install, Lenovo T500 /w SSD"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by stevenmansour on 2009-10-30
Hello,

I put in a brand new OCZ SSD hard drive and did a fresh install of Karmic 64-bit on my Lenovo T500 laptop. At first the Radeon 3650 wasn't working but I found the hacked / patched "nobackfill" xserver to fix that.

Now, however, I still have two **major** problems that are plaguing my system:

[LIST=1]
[*]The mouse / entire system will hang, usually for just a couple seconds, when I select a block of text and press "CTRL-C" to copy it. Also, the same thing happens when skipping to the next song in Rhythmbox. Hitting "Next Song" causes the system to become unresponsive. It doesn't happen always, but often, and it's pretty maddening. This happens both with and without compiz enabled.

[*]I've had three full on crashes so far. One was while opening a menu in Empathy, one was recording audio in audacity, and another while trying to record a desktop session with gtk-recordmydesktop. The mouse could still be moved, but X / everything else was dead -> hard reset.
[/LIST]

Anyone else having the same problems? :-|

---

### Post by stevenmansour on 2009-10-30
Also just notice that this happens when **pasting** text as well.

---

### Post by stevenmansour on 2009-10-30
Hmmm - looks like the mouse hang issue *only affects the touchpad*, and not when using an external mouse / red lenovo pointer. So, would that make this an issue with the touchpad driver?

---

### Post by davemb on 2010-01-07
For what its worth, you are not alone - me too. Lenovo T400, regular sata, fresh install of Karmic 64. Getting freezes at least once a week.

I just updated to the latest updates as of today and the system froze within 10 minutes of the reboot required by the included kernel update.

I was using the touchpad, so will try and note if I get freezes when not using it although I have a bad habit of brushing it when I type anyway.

---

