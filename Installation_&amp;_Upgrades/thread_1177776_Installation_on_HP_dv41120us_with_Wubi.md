---
title: "Installation on HP dv41120us with Wubi"
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by fleasbaby on 2009-06-03
Hi All,

I was keen to try Ubuntu so I tried the Wubi install on my HP dv41120us...I was wondering if anyone else ran into the same issues as me...

The wireless card seems not to work, the sound isn't working and when I boot up I get the bongos repeating for a long time until they fade away into the distance...

My wireless card is a Broadcom4322AG 802.11a/b/g/draft-n

Has anyone done an install on one of these laptops, and if so, any hints?

Any help would be much appreciated...

Thanks.

---

### Post by brayden13 on 2009-06-03
When you went to hardware drivers in System -> Admnistration it didnt' show any driver? if not then your card is probably not supported, but i doubt that, broadcom as i heard is pretty well supported, my one is supported great.

---

### Post by fleasbaby on 2009-06-03
Hmmm...well that's weird...it shows the driver there...I get a little message on the right of my screen saying Ubuntu is using restricted drivers.

If the Broadcom driver is showing there, what would be stopping the wireless from working?

---

### Post by fleasbaby on 2009-06-04
Hi All,

So the Broadcom driver runs, but I still don't have wireless. Are there any other things along the way besides the wireless card drivers that would stop me from getting wireless access?

Thanks,

---

### Post by fleasbaby on 2009-06-06
*crickets*

---

### Post by fleasbaby on 2009-06-19
Hi All,

Well, many have been my travels between the start of this thread, and far have I traveled. I have the sound and the wireless on said laptop fixed though.

The sound was a simple entry in the alsa-base.conf thingummy:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

The wireless was a case of trying to sign into my encrypted network and entering the WEP key instead of trying to use the passphrase. Go figure it would be something that simple.

Anyway, loving Ubuntu (except for the Lion King intro music).

---

