---
title: "Installed Ubuntu- half my RAM missing in Linux and Windows?"
date: 2007-03-05
forum: Hardware &amp; Laptops
---

### Post by Intertricity on 2007-03-05
Well it's been  a few weeks, I love Linux- even with the problems, I'm hoping these are just growing pains.

Anyway, I installed Ubuntu 6.10 Edgy on my hp zv6000, and started using Ubuntu more than my windows install. For some reason though, it was only recognizing 256mb of my 512mb. "Fine," I thought, "I'll just fix the RAM issue later." Well, when I booted back into Windows today, I realized that Windows was only recognizing half my RAM as well o_O;;

Well, I recalled that there were some problems with my ATI Radeon Xpress 200m video card and its memory usage, so I thought that might be it. I booted into my BIOS, and found that the memory management on the card was fine- it was doing SidePort and using its own 128mb of memory and nothing else. Also, in the system specs of the bios, it was only showing 256mb or RAM.

I really could use some help, if anyone knows what the problem is.

---

### Post by JayTee on 2007-03-05
What does your BIOS indicate is available for system memory? If you have 2 256MB DIMMS one of them could have gone bad. Power off the case, make sure you're not statically charged  (touch the frame of the computer before touching any components) unplug and reseat the memory and then boot into BIOS and see if the RAM is still unrecognized.

---

### Post by Intertricity on 2007-03-05
System memory says 256mb .. and I ended up stripping the screw out. Can't get into the ram compartment (it's a laptop).

---

### Post by Intertricity on 2007-03-05
Any ideas that may have to do with software? I remember that my Sound Blaster Extigy was being turned off by Linux when it shut down its Alsa driver, and so it wouldn't work in windows- could I have messed with something in xorg or another configuration file that switched off half my ram?

---

### Post by Intertricity on 2007-03-05
Okay, I managed to get the RAM cover open. There is, in fact, only one RAM chip in there. So it has to be something in the software.

---

### Post by Intertricity on 2007-03-05
I finally got my ram cover open, it turns out there's only one chip in there, so that crosses out the possibility that one of two chips went bad. Could this possibly have anything to do with my fglrx driver?

---

### Post by Intertricity on 2007-03-07
I finally figured out why half my RAM was showing up. It turns out that there are indeed two ram chips in my computer, but the second stick is in a separate place under the keyboard!

When I tested the computer with the stick of ram that was under the keyboard removed, the screen remained dark, so I put it back in. I realized then that I could stick it farther in before pushing it down than I previously thought. When I went back to the ram stick that was on the outside of the computer on the bottom, I realized that the ram wasn't pushed all the way in (I've never had to deal with ram in a laptop before).

I'll make a new post with a link to the website that helped me unscrew the keyboard to find the second piece of ram if others are having issues with finding it.

[http://www.dinarius.com/060913pavil.html](http://www.dinarius.com/060913pavil.html)

---

