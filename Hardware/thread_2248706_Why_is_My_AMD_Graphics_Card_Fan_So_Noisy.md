---
title: "Why is My AMD Graphics Card Fan So Noisy ?"
date: 2014-10-16
forum: Hardware
---

### Post by vincej on 2014-10-16
I AM USING Ubuntu 14.4 LTS on a Dell i7 8300 desktop. It has an AMD 5770 graphics card and I am using the AMD proprietary drivers. The system is not running hot - typically 38C. The sound is that of the GPU fan running fast. If I wiggle my mouse, it audibly runs faster and noisier for a few seconds then goes back to it's "standard" noisy self.  I have tried the Ubuntu driver and that was no better. 

Here is the weird thing: 

If I restart my system the noise goes away and behaves well all day. 

Then if I suspend the system and return the noise reappears.  The only way of getting rid of the noise is by restarting all over again. And so the cycle repeats it's self. 

Restarting is resetting something in the driver. And suspending the system is breaking something in the driver. 

But so far I have not managed to find a solution. Intuitively I believe that it is a driver issue. I am getting so frustrated that if I need a newer card then, I'll go and buy it. However I am not yet convinced that a new card will fix it. 

Many Thanks  !

---

### Post by marcodasilva26 on 2014-10-16
While this may not be the solution you can use it to monitor and create a custom fan profile

[http://sourceforge.net/projects/amdovdrvctrl/](http://sourceforge.net/projects/amdovdrvctrl/)

---

### Post by vincej on 2014-10-16
Brilliant ! It seems to be working. Everything has quieted down. My only problem is now I don't know how to use it / set it up properly. Any advice ? 

Many Thanks !

---

### Post by marcodasilva26 on 2014-10-16
That tool is primary used by overclockers, so unless you intend to overclock your gpu basically you just need to set a custom fan profile...check out the wiki [http://sourceforge.net/p/amdovdrvctrl/wiki/Home/](http://sourceforge.net/p/amdovdrvctrl/wiki/Home/)

---

### Post by vincej on 2014-10-16
One of the weird things I have noticed is that when the app is running my cpu's go crazy - kicking up to 40% of max. Is this normal ?  Can I do something about it ? 

Thanks !

---

### Post by marcodasilva26 on 2014-10-16
Not normal at all! You have something weird going on with your install/drivers.

---

### Post by vincej on 2014-10-16
ok - perhaps my proprietary amd driver should be removed ?

---

### Post by marcodasilva26 on 2014-10-17
It's worth a shot...but didnt you mentioned that you had the same behavior with both drivers?

---

