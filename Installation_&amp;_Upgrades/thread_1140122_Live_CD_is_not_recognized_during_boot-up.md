---
title: "Live CD is not recognized during boot-up"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by jheylin on 2009-04-27
I have a Dell XPS 1530 laptop and a year ago I installed 8.04 on it, my first Linux system. Instead of doing a clean install for 8.10, I upgraded and things worked fine, but recently there have been update problems (error messages, etc) and I want to do a clean install of 9.04 on my system.

I've burned three different 9.04 live CD's downloaded from three different sources on the Ubuntu website and none of them have worked. I put the CD in, it gives me an error message about 'auto-run' not working which I've read is a result of WINE trying to run it and not important, and then I shut-down the computer.

When I boot it up again, it doesn't recognize any of the discs and boots up like normal. I've hit 'esc' and 'F2' to get into the BIOS booting system, but the only things that pop up are versions of 8.10 with different kernals.

I tried wiping the hard drive with DBAN to aid in making a clean install, but even that didn't work (although I probably didn't do it right).

Any ideas on how to clean install 9.04?

Thanks!

---

### Post by Slim Odds on 2009-04-27
This topic comes up frequently.

If you cannot boot from the CD, you need to check your BIOS settings. Is the CD ROM drive working otherwise?

Did you burn it properly?

Did you check the MD5SUM's?

---

### Post by jheylin on 2009-04-29
Whew!  Sometimes I feel like I did a lot of research, but here I am again making a n00b mistake.  I updated the BIOS from A07 to A12 which helped a lot, but the real answer was hitting the F12 button.  I thought hitting any of the Esc or F buttons would do the same thing, I was dead wrong.

Thanks for all the advice!  Ubuntu 9.04 is now up and running on my Dell XPS 1530 and working better than ever.

---

