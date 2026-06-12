---
title: "monitor issue. force specific monitor"
date: 2005-01-06
forum: Installation &amp; Upgrades
---

### Post by EFDisaster on 2005-01-06
Well, silly me, I assumed everything was going just fine...

I just downloaded Ubuntu and burned it to disc and started installing it, and everything seemed to be going just great until I got to the point where it tried to load X. This machine has two video cards, an onboard AGP and a PCI... the PCI has a crazy old Sun monitor that only works at certain frequencies (fixed frequency) but all the text based install screens were showing up on the other monitor, so I assumed (stupid) that the install wasn't even seeing the other monitor/graphics card yet. So, being the first boot, I have no idea what this screen actually looks like or what the options are or if I can safely or cleanly reboot or exit from X (I used to know a keyboard shortcut to kill X, but it's been quite a while since I used Linux). I just see crazy scrolling yumminess.

So, any quick advice to get out of this screen cleanly? keystrokes? I've hit nothing so far... It isn't asking some important set-up question is it?

And then some advice on how to make this thing show up on the other video card/monitor by default?
... until I get this fixed frequency monitor set up correctly.

Thanks
 John V

---

### Post by EFDisaster on 2005-01-07
so it all started coming back to me...

switched to tty1 with Ctrl-Alt-F1 ... spent a while tweaking the XF86Config-4 (including exporting a modeline from the program I was using to get this monitor working in Windows) and now I'm all set up. Xinerama and everything! I'm posting from it now, yay!

---

### Post by fng on 2005-01-07
\o/
Welcome back to linux!

---

