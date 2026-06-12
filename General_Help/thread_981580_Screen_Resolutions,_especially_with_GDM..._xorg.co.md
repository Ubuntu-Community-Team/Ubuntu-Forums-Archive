---
title: "Screen Resolutions, especially with GDM... xorg.conf not helping, nor is xrandr"
date: 2008-11-13
forum: General Help
---

### Post by AndrewZorn on 2008-11-13
I am having a really really tough time with an install of Intrepid on this computer and a CRT.  When I install on a computer with an LCD, I never have to do this crap.

I added the mode I want to use in Xorg, and it still isn't applying to GDM.

Oh wait, it's not even working for the users... the resolution is right, but I'm trying to make it run at 75hz, like it did BEFORE I installed the ATI drivers.

Then I tried to use xrandr.  I'm simply not understanding the syntax.  I basically use the output of something like gtf or cvt, and it takes it, and I have to use stupid hex codes as a label, but trying to use addmode to get it to the list isn't working.  It says ```
xrandr: cannot find output "(null)"
```


I'm so sick of this ********.  Is there any way to FORCE, and I mean **FORCE** ONE SINGLE RESOLUTION SYSTEM-WIDE if I give all the parameters?

Everything worked dandy before I installed these "I don't see what they are talking about made-them-better" ATI drivers.  I mean seriously, VESA worked better.

This is incredibly frustrating, especially when I have two other computers with LCDs and I have never even had to research this crap.

---

### Post by vandorjw on 2008-11-13
Why are you trying to set the refresh rate to 75hz?

Can you see lines across your screen? (or is it just that in your monitor manuall its says it should run at 75?)

[I know this doesn't help solve your problem but I am just curious].

Diagnostics

1) What version of Ubuntu are you running?

2) Have you tried this command?
sudo dpkg-reconfigure -phigh xserver-xorg


Cheers - CC7

---

### Post by AndrewZorn on 2008-11-14
The computer is for my mother, so I only want to run it at 1280x960 for visibility, and at anything 60hz or under at that resolution or under there is a bad moire effect.  She might not notice it, but I do.

That, and the GDM login screen keeps running at 1600x1200, which is really small for her.

I am running 8.10, and the xorg reconfigure doesn't let you select resolutions like it used to.  I tried it so many times before I looked it up... why did they change that?  Apparently it's not flawless enough to work right without manual setup.

Seriously, it got all the right stuff with the VESA driver.

xrandr seems to be able to do what I want, add/delete available resolutions that even the resolution picker chooses from.  I just can't figure out how to use it or find a step-by-step guide, as most people in the Google results just use it for multi-monitor.

---

### Post by AndrewZorn on 2008-11-19
Wow, no one?

---

