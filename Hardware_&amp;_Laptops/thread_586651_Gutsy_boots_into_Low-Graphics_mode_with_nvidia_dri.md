---
title: "Gutsy boots into Low-Graphics mode with nvidia drivers enabled"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by jrosskelly on 2007-10-22
Hi all, just installed Gutsy on my desktop and have had problems when attempting to use the restricted drivers for my nvidia GeForce 7600 GS. After enabling them and doing the reboot it boots into Low-Graphics Mode with 800x600 res.

I'm thinking this may have to do with the fact that Ubuntu detects my monitor as a generic "Plug n Play" and isn't correctly identified as a Diamond View 771A.. But I could be wrong. I'm wondering if there are drivers available for this monitor or a way to manually insert the specs. 

Sorry if I'm missing something obvious, quite new to Linux.

---

### Post by jdwhitfield on 2007-10-24
I have the same error.  I tried changing the xorg.conf via the terminal and using the nvidia config tool but neither works.  If anyone has any insight it would be greatly appreciated.

JDW

---

### Post by Jeek Elemental on 2007-10-24
the new screenmode thing didnt quite work for me either, the font was so tiny it was unreadable, changing screenmode either hung the pc hard or made my lcd go out of range.

the odd thing is when I set mode/freq and then test, the test screen displayed fine.
but when clicking keep mode, it went out of range or locked up.

early days I guess, will be great when kinks worked out :)

I disabled restricted drivers, compiled the newest nvidia drivers and installed, working fine so far.
will be interesting to see what happens come reboot time tho ;)

this on a amd64x2 nvidia8600 ubuntu 7.10 32bit

---

### Post by jrosskelly on 2007-10-25
This is quite embarrasing but it turns out the problem was that the external power wasn't plugged into the graphics card. Must have come out at some point without me noticing..

Just plugged it in and Compiz and all is working very well. Don't know if this will be your problem but it's worth a look.

---

### Post by pappfer on 2007-11-08
@**jrosskelly**: I know it sounds weird but are you sure that was the real cause of your problem?
I'm having the same problem: after enabling restricted drivers Ubuntu (Gutsy) only starts in low-graphics mode and I can't use a resolution greater than 800x600.

It's quite frustrating considering that it always worked before.

I have everything correctly plugged, I triple-checked it. Any idea how to solve this?

---

### Post by jrosskelly on 2007-11-08
Hmm not sure really. If there is a problem with the drivers it is worth a shot to use a program called Envy to install them. It can found at [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

If that doesn't work I am out of ideas.

---

