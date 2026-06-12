---
title: "Lenovo E320: clickpad problems"
date: 2012-07-12
forum: Hardware
---

### Post by mercmobily on 2012-07-12
Hi,

I have just installed Ubuntu 12.4 (fantastic!) on my new Lenovo laptop (even more fantastic!).

The problem I am having is that the Clickpad doesn't seem to be behaving OK: if I touch the bottom left hand side to click, that's taken by the touchpad as a proper touch; the cursor will jump there, and the click won't be detected.

I looked online for a solution, but I couldn't find anything that actually solved it.

What's the actual solution to the problem? I wouldn't really want to cut off the whole bottom part of the touchpad as "buttons", as it's already small as it is...

Any ideas?

Thank you!

Merc.

---

### Post by mercmobily on 2012-07-12
Just found this:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/365943](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/365943)

That's exactly my problem! Comment #76 says:

-----------------
Created attachment 40902
Add JumpyCursorThreshold option patch v5
...
Therefore Alberto Milone's JumpyCursorThreshold option patch is still needed, which is the best solution I've seen so far. I've attached the new patch I ported to head. I've tested it in MeeGo and it works very well (with Threshold set to 250).
-------------------

The patch, that should be released, adds a settings, "JumpyCursorThreshold". But... how do I use it? What do I set it as?

Any help would be much appreciated!

Merc.

---

