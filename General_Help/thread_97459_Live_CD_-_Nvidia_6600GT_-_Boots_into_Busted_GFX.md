---
title: "Live CD - Nvidia 6600GT - Boots into Busted GFX"
date: 2005-12-01
forum: General Help
---

### Post by Ravensign on 2005-12-01
Athlon XP 2600+

The Live CD seems to work like a champ chugging along, then when X starts, I just get vertical lines, then some more crazy lines, then lock ups.

Its like the olden days when the timings were off.

I havent used Linux in 5 years, and I heard alot about ubuntu, and I thought about maybe checking things out again, but... a 6xxx Nvidia card is not remotely exotic. Kind of disappointed... is there an option on the LiveCD that allows for a more compatible Nvidia experience?

---

### Post by Edit on 2005-12-01
What happens when you hit Ctrl + Alt + F1 to get to a Console screen?

You may need to download the latest NVidia drivers for your card from [http://www.nvidia.com/](http://www.nvidia.com/) and install them via the Console.

It should be a .bin file that you download and from there you just have to chmod +x it to make it executable, then ./[filename] to run the install.

-Edit

---

### Post by Ravensign on 2005-12-02
Unfortunately, I really need a bootable ISO, ie the Live CD, so I really need to have a workable soultion, w/o the interjection of the drivers.

Does anyone know of a version of Ubuntu or Kubuntu that is 6600GT friendly striaght from the ISO?

---

### Post by v00d00 on 2005-12-08
I am very new to Linux (minimal to no experience) and I also have a 6600GT video card, and I'm experiencing the same jumbled screen.

I tried both the AMD64 and I386 versions.. everything works perfect until it gets to the desktop part (I would assume). Someone asked my what resolution it is, but it's so jumbled up and screwed up I have no idea. Nothing is percievable, though if you move the mouse you see pixels change colour, so it appears to be in a desktop environment, just displaying totally wrong.

I really hope someone can solve this silly problem. I as well don't wish to full install Ubuntu, I just want to start getting comfortable on occasion by playing with the Live version.

---

### Post by v00d00 on 2005-12-10
Update:

Here's a photograph of my screen when it finally gets into the (I assume) desktop:

If I move the mouse, some of the pixels change colour.. so it appears like it is loaded properly, but displaying completely wrong.

[img]http://img502.imageshack.us/img502/2654/linux9zl.jpg[/img]

---

### Post by v00d00 on 2005-12-13
Hmmm doesn't seem to be much help around.

Well I tried installing the full version, assuming it was something wrong with the LiveCD version(s).. but after final installation and booting up, it does the same thing.

Again I assume it's just the desktop graphics getting jumbled. Though I can't figure out why or have any clue how to resolve it.

Help please?

---

### Post by RAOF on 2005-12-13
You might want to try the VESA X drivers.  The open-source nv drivers jave some problems with the newer nvidia cards, and that's what X will be using by default.

You can boot the livecd with "live-expert", and when the time comes, change the X driver from "nv" to "vesa".  That should get a working GUI.

---

### Post by v00d00 on 2005-12-28
As a followup for anyone searching for this same issue.

I did mess around with settings and I think I may have picked VESA (I tried many different things), but eventually one of my choices did load Ubuntu properly, though at that point I had given up on the LiveCD and was dealing with the full install, although I imagine the same thing goes.

After getting into Ubuntu, I then could update the Nvidia Driver.. and works perfect now.

---

