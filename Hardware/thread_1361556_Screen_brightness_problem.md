---
title: "Screen brightness problem"
date: 2009-12-22
forum: Hardware
---

### Post by Vignesh S on 2009-12-22
Have a Toshiba Satellite T110/00D running Ubuntu 9.10 32-bit with Kernel version 2.6.32. For some strange reason, screen brightness will not increase/decrease and stays on the brightest settings when I press the hotkeys to do just that. Clearly, this is a problem because this not only sucks all the battery life out, it also burns my eyes out when I'm using this in dark places. This is really strange because:

1. Notify OSD comes up with the notifications of changed screen brightness, but nothing happens

2. It doesn't have a problem when it comes to fading to black when the screen darkens.

The graphics chipset is Mobile Intel 4 Series Graphics controller or more precisely GMA 4500M. 

My questions are:
1. How do I link up the hotkeys to change the screen brightness?
2. If the above is impossible, how do I change the screen brightness manually/hacking it to work? I don't particularly mind if I have to do it manually every time I log in, so long as I can change the screen brightness

---

### Post by Vignesh S on 2009-12-22
<bump> Surely I can get the screen brightness to change... I'm trying to avoid having to use Windows simply because I couldn't change the screen brightness in Ubuntu :-(

---

### Post by syarif on 2009-12-22
i got a simple and better solution.
its working like a charm for my computer.
You dont need to change the acpi manually.

You can seek for my post here:
[https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/392948?comments=all](https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/392948?comments=all)


:)

---

### Post by Vignesh S on 2009-12-23
hmmm.... I tried the fix, and I quite like it. But there are only the minor quibbles that it doesn't control the brightness across the whole system. 

But thanks HEAPS Syaref :-D. I guess that this issue is now solved (until the Ubuntu devs get this issue fixed up for good ;-))

---

