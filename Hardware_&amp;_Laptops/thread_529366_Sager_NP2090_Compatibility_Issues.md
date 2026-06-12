---
title: "Sager NP2090 Compatibility Issues"
date: 2007-08-19
forum: Hardware &amp; Laptops
---

### Post by Mongoose.wa on 2007-08-19
I ordered a Sager NP2090 a few weeks ago. I've just read some unsettling documentation of compatibility issues with it and Linux/Ubuntu. Apparently, many features don't function at all, including sleep, hibernation, and the memory card and fingerprint readers. 

I'm getting this info from [here](http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90/). (Compal IFL90 == Sager NP2090)

After reading the guide, it's seeming like getting my as-yet-to-be-shipped laptop to run Ubuntu flawlessly is going to be a bit more work that I originally thought. I knew I'd have to mess around with graphics drivers and the like, but not to this extent.

So, what I'm wondering is:

1. How effective is the suggested Ubuntu install in that guide going to be. It says that a normal liveCD won't work at all and that you have to use an alternate. Why is this? And is the alternate installer much more difficult to user? I've only used liveCD's in the past.

2. If sleep and hibernation aren't supported, what will happen when I close the laptop's lid?

3. Is the future apt to be hopeful for more support for the various currently unsupported features of my laptop? I'm trying to be optimistic and hoping that future updates of Linux, Ubuntu, xorg, etc will help make all the bells and whistles function properly.

---

### Post by nosrednaekim on 2007-08-19
1. seems the video card is stopping the regular CD from installing. The non-live CD is still quite easy to use, expecially if you don't have to worry about erasing windows. (Sagers as a rule come without an OS, right?)

2. nothing... your screen will blankwhen you close the lid. When you open the lid back up, the screen will tun back on.

3. looks to be... especially with video an wireless. He mentions several components which will work better with gutsy.

---

### Post by Mongoose.wa on 2007-08-19
> **nosrednaekim said:**
>  (Sagers as a rule come without an OS, right?)

Normally, but I bought mine OS-less. No sense paying an extra $100 for Windows when I won't even be using it. I have an extra copy of XP anyway, if I ever need it for some reason.

Thanks for the reply. I'm hoping I can get the sound card and wireless working without any major hitches. Most of the rest of the stuff is trivial, but would be nice to have, I suppose.

---

### Post by c1rcu17 on 2008-01-02
I have the Sager NP2090 and Gusty running right now. Just today the creator of the guide "http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90/" just tested out suspend. Supposedly it is working better than expected. Hibernation is still a no-go. I set up Ubuntu to just turn off the monitor when I close the lid. I don't even miss the hibernation and suspend functions. But that's just my preference. Overall, I have had a good experience with the Sager and Gusty. Feisty was a lot more picky with the older kernel.

---

