---
title: "Resumes to black screen"
date: 2009-12-29
forum: Hardware
---

### Post by clevertomato on 2009-12-29
My brand new Dell Studio 1555 with ATI 4570 GPU is working quite well so far. I ran the Karmic live CD before installing and it worked great. I even tried suspend and resume using live CD and it worked great.

Now, after a fresh Karmic install (amd64) it suspends but resumes back to a pitch black screen. I have to CTRL-ALT-PRTSC+R,E,I,S,U,B to shut down system then. I haven't tried activating the ATI proprietary drivers yet. That's the next thing I'll try I guess, although I've read here that those screw up suspend and resume too.

I thought ATI open source drivers were "coming of age." (I just read that thread the other day.) Anybody have any insight or solutions for me? This behavior existed immediately after install (before updates) and after all current updates.

Everything else (at least obvious things)... even the screen brightness Fn keys... work fine so far. Suspend and resume is a must-have for me on my laptop.

---

### Post by MelDJ on 2009-12-29
i use a dell 1555 too and found the open-source drivers 'not good'. so i went did a clean install and installed the drivers from the ati site

---

### Post by clevertomato on 2009-12-29
Screen brightness Fn keys were working fine with open source drivers but resume after suspend was not. Now with the ATI proprietary drivers, Fn brightness keys don't work anymore but resume after suspend does work.

Also, there seems to be no "awareness" of when I close the lid. The LCD stays on just as if I'm using it when I close the lid. I've tried setting the power management settings to blank the screen and to suspend the computer when the lid gets closed, but neither has any effect.

Anybody have any ideas?

---

### Post by clevertomato on 2010-01-06
I gave up on trying the 2.6.32 kernel with fglrx drivers right now, so I never solved the original problem of this post per se, but I got everything working that I wanted to... finally.

On my Dell Studio 1555 with ATI Mobility Radeon HD 4570 the following is working:


[LIST]
[*]Brightness keys
[*]Suspend and resume
[*]Lid closing and opening behavior
[*]3D effects
[/LIST]
 Here's what I did, for the record...

I reinstalled Karmic amd64 AGAIN. This time, out of desperation, I chose ext3 instead of ext4. I have no idea if that is related. In fact, I doubt it is. After fresh install, I installed ATI Catalyst 9.11 drivers from ATI's website (the ati*.run file). I chose automatic install with that and it completed fine. Then I applied all critical system updates, which gave me kernel 2.6.31-16, among other things. Brightness keys work, suspend / resume works, even closing the lid and reopening works. Compiz works. I'm afraid to breathe for fear that something is going to break again. I didn't have to add anything to my grub line or upgrade to a non-released kernel.

---

### Post by clevertomato on 2010-01-06
I spoke too soon, BUT, I have some very specific information that I hope someone will know how to use.

Everything was working perfectly, but today it all went to crap except manual suspend / resume still worked (from the upper right corner). Brightness keys did nothing and closing the lid did nothing. Difference? Last night I had the battery removed from my laptop. Today I have the battery back in. I removed the battery, plugged into AC cord, and it all worked perfectly again.

SO, without battery but with AC power, it all works. With battery, brightness keys and lid closure behavior stops working. I'm hoping this clue is enough for someone to come up with a solution to the problem.

**SOLVED: I added "noapic" to the appropriate line in my grub file and voila... all is right with the world again. Whew!**

---

