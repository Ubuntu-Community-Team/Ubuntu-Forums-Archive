---
title: "Weird Pixels on Screen Problem"
date: 2009-12-10
forum: Hardware
---

### Post by terminator14 on 2009-12-10
I have a weird problem that I was hoping to run by you guys to see what you think. 

A few days ago I started getting random red pixels all over my Ubuntu screen (by all over I mean in random locations but there aren't that many of them). They come and go, and are pretty unpredictable, but often stick around for a while, or even blink. Since I was using VMware Workstation 7 at the time for some school labs, I thought that might be causing the problem, but since then, I have had the same problem occur in Windows 7 as well, which points to a hardware problem since 2 completely different Operating Systems are both effected. The weird thing is that the random red pixels all disappear when I do things like open firefox (but come back when I minimize or close it), and when I move my mouse over them the mouse goes overtop of the pixels. If it was a monitor problem I'm pretty sure the red pixels would be overtop of everything. I can also take a screenshot of my desktop and capture them in the image. This points to a software problem. 

Since the first occurrence, I pulled out my video card (8800GT), and placed it into a nearby PCI-E slot (a different one than the one it was in). I thought if there was a bad connections somewhere that might fix it. This caused Windows 7 to revert back to something like 800x600 resolution, so I also completely reinstalled my nvidia driver to the newest version. The problem still occurs. I also checked my video card's temperature (with Everest) to see if it was overheating. It was about 60 degrees idle which seems ok. I tried running Modern Warfare 2 to see if it would have problems, and there were lots of red pixels during loading screens, but none in game that I noticed and the game seemed to run fine.

I'm no expert but I'm guessing it's something that's interfearing with video rendering in such a way as to make the Operating Systems think that is what the screen should look like. Sounds like something is wrong with my video card/motherboard...

[IMG]http://dxgameunit.webs.com/Pixels.png[/IMG]

---

### Post by terminator14 on 2009-12-10
BTW the Ubuntu I mentioned above is not the VM in the screenshot. I dualboot between Ubuntu Karmic and Windows 7 that the screenshot was taken in. That Ubuntu in the screenshot had nothing to do with this problem.

---

### Post by terminator14 on 2009-12-12
It's exam week and I've been too busy studying to figure out the problem so I thought I'd post here to find out what you guys thought it might be. Today I finally got some time to test a few things and I found an old NVidia X800 Pro in the basement that I swapped my 8800GT for. Seems to work fine with no red pixels anymore so I'm happy it wasn't my motherboard or monitor that was the problem. I guess it's time to get a new video card :)

---

