---
title: "Installation Errors"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by Joe724 on 2009-09-28
After my laptop died, I took my old desktop computer out of the garage and dusted it off. The parts are a little old (4+) but were top of the line when I got them and relatively hardly used. My one problem is that the hard drive with windows on it had to be replaced so I don't have an operating system and figured I would try out Ubuntu. I got a ubuntu CD from a local computer store and tried it out.
 
After unplugging and reconnecting some loose parts inside the case, I started up BIOS and did a self-diagnostic scan to see what parts were working. Everything seemed fine with that scan. I threw in the CD and tried to install it when I got some errors. I got to the Ubuntu screen where the bar moves from left to right when suddenly the screen changed to a black screen with scrolling white text. There were literally hundreds of lines of writing so I couldn't capture them all but here's an example of what one line said.
 
164.1265. Buffer I/O error on device srd0. Logical erorr...
 
but add a few hundred lines of stuff like that and ongoing for ~20 minutes.
 
I restarted and tried a couple more times but nothing worked. I tried using memtest86+ from the live install cd and my computer kept getting consistent freezes at exactly 48 seconds into the process.
 
Since I don't have a current operating system, I don't know what to do. Was there an error when the CD was burnt (I believe it was written at 16x, and speeds such as 4x seem a lot more popular to reduce errors), is it a problem with my RAM (even though BIOS is saying it's fine), is my DVD drive shot and producing these errors?, or could it be a problem with my existing hard drive? 
 
I'm at a loss for answers. I guess i'll start out with trying another cd (burned at a slower speed), then replace the stick of RAM, and if neither works swap out the dvd drive. Any easier ideas though? Unfortunately without a working OS to begin with, it makes this a lot more complicated...

---

### Post by earthpigg on 2009-09-28
> I tried using memtest86+ from the live install cd and my computer kept getting consistent freezes at exactly 48 seconds into the process.

for memtest (iso burned from the free dload at [http://www.memtest86.com/](http://www.memtest86.com/)) i had the same problem with freezing on my brand-spanking-new computer, and using the ***old version*** of memtest on the CD worked perfectly (when you start it, you get a menu that gives you the choice of current version or old version). no idea why. you could give that a shot.

couple likely possible issues you are having:

***bad RAM***. you where correct to suspect this as a possibility from the I/O issues. that's what memtest will test for, if it works.

***bad CD drive***. could also explain the failure of both memtest **and** booting an Ubuntu LiveCD.

4 years old means it can probably boot from a USB thumb drive. take a look here: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

if booting from USB works, but booting from CD does not, then your CD drive may be dying... and those things are funny because most things with computers are either **broken** or **not broken**.... not so with CD drives. i myself have had a cd drive that i could not boot from, but otherwise worked fine.

---

