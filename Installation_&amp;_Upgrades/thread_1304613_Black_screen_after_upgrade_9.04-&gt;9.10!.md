---
title: "Black screen after upgrade 9.04-&gt;9.10!"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by jerrry94087@yahoo.com on 2009-10-29
Now it boots but soon after few kernel messages screen switches to black and stays that way. Based on disk activity I know it boots, just the screen is black. Ctrl-Alt-F1 doesn't switch to text either.

Looks like this is a problem with graphics. I have i810 chipset. The only thing is that before, in 9.04, I had some graphical artifacts (damaged fonts) and I followed instructions here [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4) to downgrade.

After upgrade to 9.10 I figured I have to restore original xserver-xorg-video-intel, so I uninstalled xserver-xorg-video-intel-4.2 and installed xserver-xorg-video-intel.

Should xserver-xorg-video-intel be installed in 9.10? Is xserver-xorg-video-intel supposed to be installed on 9.10?

Loading previous kernel 2.6.28 instead of a new one 2.6.31 makes graphics to come back. But mouse is dead.

How to make it work?

---

### Post by jessiebrownjr on 2009-10-29
This wasn't fixed? its been an issue for a long time, why I couldn't upgrade on my laptop as well :-(...

I hope there is an easy fix!

---

### Post by jerrry94087@yahoo.com on 2009-10-29
I scrapped Ubuntu.
Installed back Gentoo, it works on the same system flawlessly.

I think 9.X series is really flawed.

---

