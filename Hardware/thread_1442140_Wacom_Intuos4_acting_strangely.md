---
title: "Wacom Intuos4 acting strangely"
date: 2010-03-29
forum: Hardware
---

### Post by jethro1138 on 2010-03-29
Hi all!

I just got a Wacom Intuos4 which I've been craving for a while. Last time I had a wacom tablet was an Intuos2 a million years ago, and that was a PAIN to set up under Linux, so I was VERY happy when I plugged this thing into my Ubuntu 9.10 machine and it just worked. I didn't even have to restart X! 

Except it... kinda does some weird things.

...which are probably to do with my weird setup.

 Two of them, running on the same video card, are set up as nVidia TwinView, and the third is a separate display, and on a separate video card. Xinerama is on, so I can move things between all three displays. The setup looks like this:

[ 3 ] [2][1]

Where 1 and 2 are TwinView, and set as th primary screen.

I like this because it means I can do full-screen video on Display #3 without it distorting and taking up two monitors. 

Anyway, when I use the pen on the Wacom tablet, starting at the very righthand side and moving left, it'll move the entire width of screen #1, then get to about a third of screen #2 and jump to the last third of screen #3.

The mouse is even stranger. It'll work fine when it starts out in screen #3 and will cross back into screen #2, but it can't go from #2 to #3. 


I can't seem to find any answers online, probably because of my crazy setup.

I will note that I haven't done ANYTHING to my xorg.conf when I got the wacom. There are absolutely NO definitions for it. It Just Works(tm).

I've tried the tools that come in the wacom-tools. wacomcpl seems to not see any devices, and I can't seem to figure out how to tell xsetwacom to do anything. The documentation that comes with this package is pretty ancient. wacdump DOES identify the device, but doesn't show any status changes.

Anyone have ANY ideas?

---

