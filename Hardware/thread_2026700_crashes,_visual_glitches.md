---
title: "crashes, visual glitches"
date: 2012-07-15
forum: Hardware
---

### Post by heinz57 on 2012-07-15
Hi,

So, my computer crashed with a BSOD. I had just turned it on and was web browsing. And now as soon I turn on it on I get a pattern of blue dots on the screen. And if I go into the BIOS there's random glitchy characters everywhere, but the blue pattern disappears. I can't boot into ubuntu or windows, they give really weird graphical glitches and then crash. Windows safe mode works though.

Anyone else ever have a similar problem? Is this a problem with the video card/motherboard/BIOS/something else?

---

### Post by Bucky Ball on 2012-07-15
Sounds like hardware trouble of some kind, yes. The fact Win works in safe mode is a clue. Maybe graphics but that is guessing. 

Can you boot into Win safe mode and switch off the graphics card (or take it out) then see what happens when you boot?

---

### Post by ahallubuntu on 2012-07-15
There are many potential causes of blue screens (in Windows) and freezes/random crashes.  If you see them in Windows and you have similar freezes in Ubuntu and they started at the same time, it is almost certainly related to hardware.

It could be any of these, including but not limited to: hard drive, power supply, CPU (overheating), RAM, or motherboard.

Basically, you try to test/rule out everything but the motherboard; if nothing else is wrong, it's probably the motherboard.  It's not practical to test the motherboard, but you can inspect it visually for signs of bulging capacitors.  (Google for "blown caps" to see pictures of examples.)  If the motherboard is bad, it's usually not worth replacing.

First thing I test in cases like this is the hard drive - check the S.M.A.R.T. status because it's good to check S.M.A.R.T. once in a while anyway if not constantly monitor it as I do.  You can check S.M.A.R.T. with a Parted Magic CD (a nice light little distro you can use for basic debugging stuff).  Click on "SmartControl" after you boot up Parted Magic and look for Attributes highlighted in Red.  If you see any highlighted, tell us what they are; a failing hard drive could most definitely cause these kinds of blue screens.

Check the CPU to make sure the fan is working and that the heat sink isn't clogged with dust and dirt.  This is especially true if the computer is more than a year or two old.  CPU overheat more likely if the crashes occur more frequently once computer is warmed up.

Check the RAM - try running Memtest (on any Ubuntu CD).  Let Memtest run for at least a few minutes; if it doesn't crash, the memory is probably OK.

(Desktop only)  Power supplies are more tricky to test without a tester.  Sometimes swapping in a different one is easiest to try, if you can borrow one known to be good.  Check that the power supply fan is working, too.

If everything else tests out, motherboard is very likely the problem even if you don't see bulging, blown caps.

---

