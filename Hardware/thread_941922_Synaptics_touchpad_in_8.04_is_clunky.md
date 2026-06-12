---
title: "Synaptics touchpad in 8.04 is clunky"
date: 2008-10-08
forum: Hardware
---

### Post by peppergrower on 2008-10-08
I've been playing with Ubuntu server edition from the command line for a while now on an old machine, and decided to set up my primary machine as a dual-boot (XP and 8.04).  I like quite a few things about Ubuntu, and I'd love to make it my primary OS.  I have a Dell Inspiron E1505 with a Synaptics touchpad.

However, the behavior of my touchpad is really frustrating. Here's what I'm looking for solutions for: in Windows I've gotten used to having immense control when making small/slow movements; in Ubuntu, the sensitivity is too high when I'm making small movements but not high enough for across-the-screen movements.  (There's no way to get both.)  In Windows, the touchpad registers every tap as a click, but not accidental touches; in Ubuntu, it only registers about half of my taps, but far too many of my accidental touches.  And finally, in Windows if I use the touchpad to scroll (by moving my finger along the edge of the touchpad), the scrolling stops when I stop moving my finger.  Also, if I move my finger rapidly, the application I'm in scrolls rapidly (or even jumps to the top/bottom of the page, if I move it really fast).  In Ubuntu, it seems to be registering a number of scroll events, and the screen keeps on scrolling until it's handled all of those--even if I stopped trying to scroll a couple seconds ago.  And it scrolls at the same rate whether or not I drag my finger swiftly or slowly--it just keeps scrolling for more or less time.

I love many things about Ubuntu (I really do), but for one of my main interfaces to be so clunky...it makes it hard to want to keep using Ubuntu, even with all the other features that are much better than Windows.  I've installed the gsynaptics package and played with the settings there, but didn't find anything to address these issues.  I suspect it's the driver implementation itself...but is there anything I can do?  Some obscure command-line magic, or perhaps different drivers, or something?

---

### Post by peppergrower on 2008-10-11
I guess the fact that it's been three days with no response means no one has any suggestions...  Perhaps most people don't have a problem with the current touchpad drivers?  One last try: does anyone have any ideas for ways I can improve my touchpad's response?

---

### Post by ricpat51 on 2008-10-12
Hey man,
I've been facing the same problems you have. And I'm desperately searching for a solution for it. I think the issue is in the fact that on Windows we have the software that provides the extra features like sensibility and those things you mentioned. But I think it must be a solution to our case and I hope someone could give us a light here. If you find something, please let me know ok?! I do the same.

best regards

Ricardo.
P.S: Sorry for my English, it's not my first language.

---

### Post by Megakazbek on 2008-10-12
I have 8.10 beta, not 8.04, but I too find the touchpad behaviour very uncomfortable, unlike in Windows where it's very nice and natural. As described here, the sensitivity is not enough for small movements. Also, I got lots of accidental touches when typing (and I NEVER got them in Windows), and sometimes they lead to horrible things like accidentally clicking a button in a dialog window. Actually, one of such accidental touches almost deleted my Windows partition during Ubuntu installation! So this may seem like a minor problem, but in reality it could lead to very critical issues that could damage the whole system. So I really seek for a solution to it.

---

### Post by fifteen10e56 on 2008-10-14
I'm in the same boat.  I just switched to the 8.10 beta in the hopes that it would be better with little success.

My laptop's a Dell D630 which (I believe) uses an Alps touchpad, though I'm using the default touchpad driver (synaptics, I think).

---

### Post by ricpat51 on 2008-10-22
There should be some configuration file to fix these features I think.
If someone find out something please just post here because this touchpad's problem sometimes upset me a lot.

Thanks for all

---

