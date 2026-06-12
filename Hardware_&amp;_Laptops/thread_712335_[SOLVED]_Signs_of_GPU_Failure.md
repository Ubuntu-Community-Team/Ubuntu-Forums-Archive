---
title: "[SOLVED] Signs of GPU Failure?"
date: 2008-03-01
forum: Hardware &amp; Laptops
---

### Post by ph1 on 2008-03-01
I've been noticing some weird things since I've installed Ubuntu on my laptop back in December.  First, my screen would sometimes "spasm" and be completely unusuable--all smeared out in colored streaks, though you could sort of see the window's color underneath, e.g. if I hit "alt-F4" to close my browser, the white of the webpage would be replaced with my desktop background.  Rebooting was the only thing that fixed this.

Now, I've noticed that along the bottom of the screen, perhaps half a cm above the taskbar, a small horizontal line appears sometimes across the screen.  It "absorbs" the color of the pixels above it, so if I have my black cursor somewhere above it and I move it, a black smear on the line moves under it.

The line appears when I first boot the computer up--before it's even done loading the BIOS.  It also appears in Windows when I (mercifully rarely) boot into that.  

I've had a couple of "heat scares," especially since Linux didn't seem to be very efficient at controlling my fans before i8k let me take over, but I'm told that GPUs can be intact up to 70, even 80 degrees C, and I haven't exceeded those temperatures, to my knowledge.

Any opinions on what might be going on?  Should I be worried?  I've got a great warranty--if worst comes to worst I'll backup Linux, reinstall Windows, ship my notebook off to get it fixed--but I don't want to go through several weeks of school without it.

---

### Post by information_entropy on 2008-03-01
Boot from the live CD and run memtest86 and make sure your memory is OK.

Or, you may be suffering from the rare Golden Ratio Failure Syndrome :-P

---

### Post by ph1 on 2008-03-01
Good idea, I'll give it a try before I give up hope.

Hopefully the golden ratio failure syndrome hasn't broken anything....I don't think computer handle irrational numbers well......

EDIT:  99% sure it's not the RAM that's the issue.  I'm still convinced it's the GPU.  Any other advice?

---

### Post by ph1 on 2008-03-01
After further investigation I've determined it to be a loose wire in the LCD panel.  When I swivel it back or forward, I can make the line appear of disappear, and it's just one line across the screen.  Now, how to fix that.....

---

### Post by information_entropy on 2008-03-01
Thats good news, I think.

---

