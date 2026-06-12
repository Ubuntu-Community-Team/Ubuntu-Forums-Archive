---
title: "Touchpad won't play nice"
date: 2011-03-07
forum: Hardware
---

### Post by funkwurm on 2011-03-07
OK so in trying to solve a problem I introduced a new one, so let me start from the beginning.

I have a MacBookPro1,1 running Ubuntu 10.04, I'm aware of the Apple users forum but I believe this is more a Synaptics driver/settings related problem.

The touchpad has 2-finger scrolling capability which I really like under Mac OS and it's kinda working under Ubuntu but I was trying to make it work better.

What happens with a default Ubuntu install is when you don't put down both fingers at the EXACT same time on the touchpad, a scroll-event fires. What I would like is that there's no scrolling as I put the 2nd finger down on the pad, but only when I actually drag both fingers over the pad.

My first hope was that gpointing-device-settings would let me set some threshold, but it doesn't. However now that I installed it both my secondary and middle click are disabled. It used to be that I could place 2 fingers on the pad and click the button for secondary, and place 3 fingers + click for middle click. That is now gone and I'm trying to get it back first of all but I can't find anything.

All I find is about "3 mouse button emulation" but that is where you press left and right simultaneously, which doesn't make sense as the Mac touchpad only has 1 button to begin with.

What file does gpointing-device-settings change anyway? It doesn't seem to be any of the files in /usr/lib/xorg.conf.d/ and I don't seem to have any other xorg.conf-ish files.

I've found this: [http://kubuntuforums.net/forums/index.php?topic=3113349.msg239420#msg239420](http://kubuntuforums.net/forums/index.php?topic=3113349.msg239420#msg239420)

But non of the settings in that custom .conf file tackle either of the problems I now have (scroll on 2nd finger-on-pad and no secondary/middle click)

---

