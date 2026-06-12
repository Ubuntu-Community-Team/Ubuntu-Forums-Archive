---
title: "Graphire4 tablet works only on Xorg restart"
date: 2007-06-27
forum: Hardware &amp; Laptops
---

### Post by otakuj462 on 2007-06-27
Hi, I recently acquired a Wacom Graphire4 drawing tablet. I replaced the relevant lines in my xorg.conf file with those found [here]("http://ubuntuforums.org/showthread.php?t=25151"). The tablet now works (pressure sensitivity and everything -it's great), but only if I plug it in, and then restart X. When I first plug it in, I can tap it with the stylus, and this registers on the screen, but moving the stylus above the tablet does not change cursor position, and absolute positioning does not work.
If anyone can offer any guidance as to how I can get this to work on hotplug, please let me know.
Thanks.

Jake

---

### Post by dsmithhfx on 2007-06-29
The Wacom drivers (in various incarnations) don't currently support hot-plugging, from what I've read. There may some sort of hack. Check on [http://linuxwacom.sourceforge.net/index.php/main](http://linuxwacom.sourceforge.net/index.php/main) about that...

But I have a question for you: Apart from the hot-plugging issue, does the graphire 4 work "out of the box" (after changing xorg.conf)? What version of Ubuntu are you running it on?

I'm thinking of replacing my old pen partner serial tablet with the graphire, because the config hassles seem a little over the top (ok, waaaaaaaaay over the top), and it's nearly worn out anyway.

---

### Post by otakuj462 on 2007-06-29
Except for the hotplugging issue, after fixing up my xorg.conf the tablet worked OTB: pressure sensitivity, the extra buttons on the pen, everything that I've needed to use has worked. If there's something in particular you would like me to test, please let me know and I'll test it.

Jake

---

### Post by dsmithhfx on 2007-09-06
> **otakuj462 said:**
> If there's something in particular you would like me to test, please let me know and I'll test it.

Jake

I (finally) did get the Graphire 4 and got it working after some xorg.conf changes... but I don't have the pen or tablet buttons (including tablet scroll wheel) working. Can those be defined in xorrg.conf?

---

