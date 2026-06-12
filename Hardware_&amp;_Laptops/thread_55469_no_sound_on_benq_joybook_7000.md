---
title: "no sound on benq joybook 7000"
date: 2005-08-09
forum: Hardware &amp; Laptops
---

### Post by seigologies on 2005-08-09
i am a new user ubuntu..
dont know how to make my labtop have sound so for some one plz help me..
and one more thing.. i cant play mp3..

---

### Post by Frankk on 2005-09-26
I had the same problem.
1st of all check that you dont have the "snd_intel8x0m" module loaded. That caused a lot of problems to me. The card works (almost) fine with "snd_intel8x0".

Then you have to check "Spread Front to Surround and Center/LFE" in your ubuntu mixed (should be the same under kubunto kde mixer). Then you can control your master volume with "Master Surround". Beware that when you plug your headphones your speakers are not muted.

That's the only way i managed to make it work...

Hope it helps.
Frankk

---

### Post by seigologies on 2005-09-28
tq for help..
how to load "snd_intel8x0m"
where i can get "snd_intel8x0m"

---

### Post by Frankk on 2005-10-04
do:

lsmod |grep snd_intel8x0

if you don't see snd_intel8x0m in the output then it's ok.
Otherwise add snd_intel8x0m at the end of /etc/hotplug/blacklist

---

### Post by Nightfall on 2005-10-05
Same problem here.

Try this (worked for me):

[http://www.cancullet.org/benqjb7000/BenqJB7000_linux.html#sound](http://www.cancullet.org/benqjb7000/BenqJB7000_linux.html#sound)

My speakers began working when I replaced my kmixctrlrc with

 [http://www.cancullet.org/benqjb7000/kmixctrlrc](http://www.cancullet.org/benqjb7000/kmixctrlrc)

---

### Post by Frankk on 2005-10-05
I believe that those config file do exactly what I sayd:
make sure that "Spread Front to Surround and Center/LFE" option is checked. Once you have done this you can contro your master volume with the "Master Surround" slider (make sure that master surround is not muted).

---

### Post by seigologies on 2005-10-09
thank a lot, it's works frankk

---

### Post by pekole on 2007-01-30
I have got the same notebook, and tried the hints above, but had no success. I tried both suggested ways.

Maybe i changed some settings when I tried to fix it on my own.
However, the headphone jack works fine (it worked out of the box).

Can somebody help me?

---

