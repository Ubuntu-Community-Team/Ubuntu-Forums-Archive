---
title: "Closing Lid &gt; Dell Studio 15 + ATI Mobility Radeon 4500"
date: 2009-12-29
forum: Hardware
---

### Post by clevertomato on 2009-12-29
I've read a lot on the Dell Studio 15 with ATI Mobility Radeon 4500 series issues. I'm running Karmic amd64 with all updates to date and experience the following problems:


[LIST]
[*]Open source ATI drivers allow the Fn keys for screen brightness to work, but resume-after-suspend sticks on a pitch black screen, requiring hard reset (or ctrl-alt-prtsn+r,e,i,s,u,b).
[*]ATI proprietary drivers via System/Administration/Hardware Drivers allows resume-after-suspend to work but the screen brightness Fn keys no longer work.
[*]The system doesn't recognize when the lid is closed no matter which drivers I use.
[/LIST]
Like I said, I've searched and read a lot, including the following: [https://wiki.ubuntu.com/LaptopTestingTeam/DellStudio15](https://wiki.ubuntu.com/LaptopTestingTeam/DellStudio15) which states that lid closure DOES work in Karmic on the Dell Studio 15... not for me.

I've tried different combinations of "noapic", "acpi=off", and "acpi=force" with no success. Any help would be greatly appreciated because I consider suspend / resume to be a critical feature for me, but also consider lid closure and the screen brightness Fn keys to be important as well.

update:
I just tried the ATI fglrx drivers from the ATI website, Catalyst v 9.12. I tried the package generation first but it failed. Then I installed using the Automatic uption. It installed, but didn't fix anything I needed to be fixed. Fn keys for brightness don't work and system is unaware of lid closure (and does nothing when that event occurs). UGH! I'm quite frustrated now.

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

### Post by darkksyde on 2010-01-06
Similar problem with dell studio xps 16, fixed by flashing bios

---

### Post by clevertomato on 2010-01-06
I spoke too soon, BUT, I have some very specific information that I hope someone will know how to use.

Everything was working perfectly, but today it all went to crap except manual suspend / resume still worked (from the upper right corner). Brightness keys did nothing and closing the lid did nothing. Difference? Last night I had the battery removed from my laptop. Today I have the battery back in. I removed the battery, plugged into AC cord, and it all worked perfectly again.

SO, without battery but with AC power, it all works. With battery, brightness keys and lid closure behavior stops working. I'm hoping this clue is enough for someone to come up with a solution to the problem.

**SOLVED: I added "noapic" to the appropriate line in my grub file and voila... all is right with the world again. Whew!**

---

