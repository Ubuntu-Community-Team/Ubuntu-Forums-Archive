---
title: "Help! Priamary dual boot Ubuntu broken!"
date: 2008-12-01
forum: Illinois Team
---

### Post by soundfonix on 2008-12-01
Ok, here's the deal. Hating Vista on my new computer, and after a few crashes of it, I dual booted Ubuntu (Feisty, then upgraded fine to Gutsy). New to Ubuntu and linux I hoped to use it most so I set it up to be the primary OS, Windows Vista secondary. 

Worked fine for a while. Some time after upgrading to Gutsy had some problems... not sure if it was before or after Heron came along but things went wacko. 

Long story short, if I can log into Ubuntu (super big resolution from the start) and nothing works right. I can't open anything without it freezing up. For a while it would get online and I went through a few times trying to run updates hoping it would fix it. 
Now when I get in just about nothing responds (and if it does it freezes shortly after) I can't even get a terminal up!!!
My Vista has been working find (surprisingly) and since I had precious grad school work riding on it I've just used that the last few months and all but forgot about linux.
School's coming to an end and I want to fix this!!!

Any clues?  

Can I re-install Ubuntu from a disk without loosing my existing secondary Windows partition? (same hard disk, by the way)
If so, how?
I know... I'm a N00b... have mercy.

---

### Post by gdeer81 on 2008-12-04
Have you posted this in the support forums?  The loco forums might be limiting the views it will get versus the general support forum.

I'm probably 100 times the noob you are (first distro is 8.10) but I've trolled the support forums enough to know what you'll need to do to get this resolved.  First you'll have to drop into grub or boot command prompt and print the result of some log.  Then based on that you'll have to find some other log.  After that you'll have to type in a sudo script and report the result of that.  In the end it will turn out to be a bug that hasn't been fixed yet.

results may vary

---

### Post by caljohnsmith on 2008-12-04
Since you say that reinstalling Ubuntu is an option, I think that is probably your best bet at this point. When you go through the Ubuntu installer on the Live CD, choose the "manual" partition option, and there you can make sure Ubuntu gets installed over your previous Ubuntu partition. In case you want to see some screen shots of what to expect, you might want to check out this tutorial:

[http://www.herman.linuxmaniac.net/p23.html](http://www.herman.linuxmaniac.net/p23.html)

How about giving that a shot and let us know how it goes.

---

