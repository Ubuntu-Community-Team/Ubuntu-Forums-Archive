---
title: "Upgraded from 9.04 to 9.10 help"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by b.jonkers on 2009-10-30
Hi all.  

Am still really new to this and i have had trouble with my upgrade.

I did the upgrade and all went well.  I had no errors or anything.  

Now when I boot my system I get a white ubuntu logo and all is going well then it jumps to a command line and my screen starts flashing and it does not always accept key strokes

i have restarted a heap of times and it still does the same thing.  so hit esc to get all the options for the grub loader and i have a heap of different kernels i can choose from.

the 1st one is 9.10 kernel 2.6.31-14-generic which I assume is the default one as the same thing happens if I select it.

The next one down is 9.10 kernel 2.6.28-16 generic and it loads and I can log in but my mouse does not work and nor does my keyboard once I am logged in.

If this has been covered sorry I have searched a heap today trying to find a solution.  Probably something I have done wrong and I just can not work out what.

---

### Post by b.jonkers on 2009-10-30
Fixed.

well for the most part.  Worked out how to navigate around to where i wanted to be in the recovery mode and then reinstalled the nvidia drivers.

All is good now for the most part.

---

### Post by motorbelly on 2009-11-01
> **b.jonkers said:**
> Fixed.

well for the most part.  Worked out how to navigate around to where i wanted to be in the recovery mode and then reinstalled the nvidia drivers.

All is good now for the most part.

Any deeper explanation you can make about what worked for you would help the rest of us less fortunate.  ;)

---

### Post by fedexfrt357 on 2009-11-06
> **motorbelly said:**
> Any deeper explanation you can make about what worked for you would help the rest of us less fortunate.  ;)

It sure would, I have the exact same problem as we speak ... :(

---

### Post by witeshark17 on 2009-11-06
I'm not familiar, but for what it's worth, I suggest a Google on the configurations and drivers on that video card for 9.10

---

### Post by fedexfrt357 on 2009-11-06
Thanks, I'll do that... :)

May I ask tho...? 
What is the difference between these...? They both show up at boot
9.10 kernel 2.6.31-14
9.10 kernel 2.6.28-16...
As the 31-14 is the one giving the issue, 28-16 seems to boot fine

---

### Post by witeshark17 on 2009-11-06
> **fedexfrt357 said:**
> Thanks, I'll do that... :)

May I ask tho...? 
What is the difference between these...? They both show up at boot
9.10 kernel 2.6.31-14
9.10 kernel 2.6.28-16...
As the 31-14 is the one giving the issue, 28-16 seems to boot fine Those are the 2 boot options. 2.6.31-14 is the newer kernel, the one you want. If it boots up on that, that's good.

---

### Post by fedexfrt357 on 2009-11-06
Got it fixed with the help of this thread... [http://ubuntuforums.org/showthread.php?t=1305459&highlight=flash+boot&page=3](http://ubuntuforums.org/showthread.php?t=1305459&highlight=flash+boot&page=3) 

#28

Thanks
:)

---

### Post by witeshark17 on 2009-11-06
Cool! Glad you got it sorted!

---

