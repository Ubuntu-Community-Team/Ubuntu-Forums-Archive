---
title: "X Windows not able to run"
date: 2005-06-20
forum: Hardware &amp; Laptops
---

### Post by GrootBrak on 2005-06-20
I have just installed Ubuntu for the first time ever. Never knew how to work with LINUX or UNIX, only windows and some DOS. I don't have the slightest clue how the commands, that's so often referred to, works.

So as a complete newbie, I installed UBUNTU from a CD quite succesfully along with my old XP, but on a new disk. No surprises, I can switch back and forth between the two. GREAT start. 

Problem is when I start Ubuntu, I get the silly, cannot start X windows, thingy. I've read about how to re-install it as a root user. Doing the "suso" thingy, I was asked to set a new password, I pressume that is OK. But trying to run the command to re-detect my hardware, gives me a "permission denied" after some other long incomprehensible clutter. Maybe I have the wrong way of setting the password, or the wrong commands. So if anyone can please explain step by step what and how and where I should type in what, that would already help. I have tried some of the examples of commands here, but nothing works.

I have an Intel System that is shown as LINUX compatible, (and XP and WIN2000)
but the Xwindows keeps on bumming me out. What is X Windows to start with? I have re-run the complete setup, but once I get to the bit of my graphics, I do not know what to use. My chipset is stock standard Intel GEV something, so I cannot seem to find it on the installation options. I did try a few different settings, but it take really long to run the complete setup  every time, so for now I keep on using XP. (Sighhhhh.....)

Regards

---

### Post by intangible on 2005-06-20
So you can log into the console?

Try this:
**sudo dpkg-reconfigure xserver-xorg**
When it asks what driver to use, try "**vesa**" that should work on everything.

---

