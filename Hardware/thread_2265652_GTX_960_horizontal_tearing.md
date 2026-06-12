---
title: "GTX 960 horizontal tearing"
date: 2015-02-16
forum: Hardware
---

### Post by Vadim_Banev on 2015-02-16
Greets all!

So long story short, I got a new desktop machine recently, with a Gigabyte GeForce GTX 960 and installed the 346 proprietary drivers. (the computer has an i7 CPU and its video controller is disabled in bios) There is some tearing in XFCE both with and without compositing enabled, but I've never really had a tear-free desktop, so I wouldn't normally bother with that. However, there's some very peculiar behavior when it comes to heavy-duty performance. Things like Minecraft (yes, I know ..) or Quake 4 give me great performance and there's no tearing that I can see. Running quake1 with the darkplaces engine or quake2 with the q2pro engine also looks just gorgeous. 

Video decoding performance is where I first noticed the problem. XV output with Mplayer gives me random tearing here and there, which was a bit of a letdown. Playing a video of any kind with VDPAU decoding is absolutely fine, as long as there's no other process making use of the video card. If I have another video running and then try to play another one, there's some random tearing, and one very glitchy persistent tear in the top half of the screen. Video file size, resolution etc is of no consequence. The same thing happens if say flash video is running in my browser with hardware acceleration enabled, or if anything else is adressing video acceleration as far as I can tell ...

 
 
 So I started testing out things I know worked fine with my older desktop and the good-old 9500GT. I dug out that loki port of Unreal Tournament and sure enough, the same persistent tear at the top half of the screen is there. Otherwise performance is perfect. Quake3 performance is lovely, but there's quite a bit of tearing in that as well.  

The machine is based on a Gigabyte Z97-HD3 motherboard with a core i7 4790, 8 gigs of hyperx ram, currently three sata hdds inside.

 
 
 I'm not quite sure how to proceed, but at this stage I'm mainly concerned with the  problem being caused by some kind of hardware conflict or even defect. Any input would be greatly appreciated, thanks!

---

