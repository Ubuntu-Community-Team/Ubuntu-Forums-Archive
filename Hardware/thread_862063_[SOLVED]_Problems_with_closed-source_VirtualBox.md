---
title: "[SOLVED] Problems with closed-source VirtualBox"
date: 2008-07-17
forum: Hardware
---

### Post by kovankerckhoven on 2008-07-17
Hi everyone :)

I'm using Ubuntu 8.04 Hardy on a MEDION Laptop (not a well-known brand), and I used to have Windows Vista installed on it, but then I got the courage together to put linux on it :lolflag:
Everything kinda worked fine up until now (the usual small hardware problems), but there is one major problem that I can't solve yet.

On my Vista, I could play Command & Conquer 3:Tiberium Wars without any problems. (sometimes ran a little slow, but the computer could handle it.)
I now have VirtualBox closed-source installed, 'cause I couldn't get the USB support working with the OSS :), and with windows XP installed on it, it's running quite smooth. 

However, when I try to play CNC3: Tiberium Wars inside the windows XP, it says I don't have 'DirectX 9.0 or above installed', my video card isn't of enough capacity, or hardware acceleration has been disabled. I've tried maxing up the video memory settings in VirtualBox, but It still won't work. I've installed the DirectX he asked for, and I checked if hardware acceleration was enabled; and it was.

Any help on this matter would be really appreciated :(

---

### Post by 505 on 2008-07-17
Virtualisation software doesn't support advanced graphic stuff. E.g., I have Ubuntu in VirtualBox but it can't do all the fancy Compiz stuff.

---

### Post by kovankerckhoven on 2008-07-17
So I won't ever be able to get it to work?

---

### Post by Vivaldi Gloria on 2008-07-17
> **kovankerckhoven said:**
> So I won't ever be able to get it to work?

Virtualbox has limited video support. So it won't work if it's a 3D game.

---

### Post by kovankerckhoven on 2008-07-17
Thx for the advice.

---

### Post by mlentink on 2008-07-17
You have to realize that a virtual machine cannot know in advance which hardware it will be run on, neither can it know what OS it will have to run. What the makers do is use a sort of a common denominator which they implement. So it'll be a very standard network-adapter, a very standard graphics adapter and the rest. Most don't even support USB (like the open source version of VirtualBox, the closed source version does)

---

