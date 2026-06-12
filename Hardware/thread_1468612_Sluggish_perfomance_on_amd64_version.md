---
title: "Sluggish perfomance on amd64 version"
date: 2010-05-01
forum: Hardware
---

### Post by MeanEYE on 2010-05-01
I had Ubuntu for years on my desktop computer but only now I decided to put amd64 instead of 32bit version. Now my compiz is sluggish. Desktop cube rotates but somehow it feels like low frame rate.

Like I said, never had this problem before with 32bit version. Anyone experiencing the same with nVidia 6150 (or any other card) on Lucid?

I did however import compiz configuration I've exported before doing clean install :D... maybe that is causing the problem... not sure... let me know what you think.

---

### Post by NightwishFan on 2010-05-01
Nvidia 6150 is fine for me on either. I get great performance (considering the card itself is not great).

---

### Post by MeanEYE on 2010-05-01
Yeah, card is far from good... but still... I think I had higher framerate on 32bit or it could easily be me... :)

---

### Post by prshah on 2010-05-01
> **MeanEYE said:**
> amd64 instead of 32bit version. Now my compiz is sluggish. Desktop cube rotates but somehow it feels like low frame rate.

I'm running a fresh 64bit install (since today!), and everything works just as well (if not better) than my 32bit install. I too am using an nVidia, but a GeForce 7300.

Note that many say that 64bit has higher RAM requirements (not that I am finding it so); also keep an eye on your "top" output for a few mins to see if anything is eating those CPU cycles.

---

### Post by MeanEYE on 2010-05-01
:/... I've checked everything... 

Even did a Compiz Benchmark. My FPS is around 32 all the time... Expo plugin is choppy as hell :(. 

My processor is acting weird. For example when I open system monitor I can see that only gnome-system-monitor takes 20% of my CPU :/. That is not what I've expected from 64bit version of Ubuntu.

If someone has explanation for this... I'd like to hear it. By the way... processor is AMD Athlon 3200+ ... I know it's not top of the line... but still :/

---

### Post by NightwishFan on 2010-05-01
Then monitor always eats cpu, try top in the terminal. However if 32-bit works better use it. :D

---

### Post by MeanEYE on 2010-05-01
Yeah, am thinking the same thing. Although... it's quite pain in the **** to get everything installed again :D... It's not unusable but... Idk... thanx for your help :D

---

### Post by NightwishFan on 2010-05-01
I have never known a difference between 32-bit and 64-bit, but if I have a 64-bit processor I plan on using it all.

EDIT: To save time on setup, make a separate /home partition, that way preferences and data are intact.

---

### Post by MeanEYE on 2010-05-01
> **NightwishFan said:**
> I have never known a difference between 32-bit and 64-bit, but if I have a 64-bit processor I plan on using it all.

EDIT: To save time on setup, make a separate /home partition, that way preferences and data are intact.

Hehe, thanx for you help. I know that already. Am a long time user...

Difference between 32bit and 64bit is actually using 64bit processor registers (in 32bit mode each register can accept 4 bytes of data while in 64bit, well 8). This enables you to use more than 3GB or RAM and many other neat stuff regarding calculations, resource addressing, etc. In theory, there shouldn't be any difference in speed but am speculating now that drivers might not be optimized or something like that. 

All in all, after some fine tuning, everything seems to be running more smoothly than before.

---

### Post by MeanEYE on 2010-05-02
Just in case someone is wondering. I've just installed 32bit version and I have 100+ frames per second (in comparison to barely 30 on 64bit). This is a HUUUGE difference.

Anyway, am staying away from 64bit version for the time being. :)

---

### Post by NightwishFan on 2010-05-03
Sure, glad it works for you.

---

### Post by MeanEYE on 2010-05-03
Oh, and it's true... Memory usage is nearly double. On 32bit, my average memory usage (with apache, mysql, browser, chat and all that things) is around 500MB while on 64bit, browser and a chat = 900MB o_0... 

Although when I checked system monitor browser and chat took about the same amount of memory. Could be that some system services eat more than they should on 64bit version... 

Bleh, :D it's working now... so :D am happy :P also I had an excuse to kill that pesky old windows partition lying on my hard drive :D

Cheers people!

---

### Post by NightwishFan on 2010-05-03
That is fine, memory usage is really irrelevant unless you have memory leaks.

---

### Post by MeanEYE on 2010-05-03
> **NightwishFan said:**
> That is fine, memory usage is really irrelevant unless you have memory leaks.

It is relevant... With those extra 400 megs being used I can run more things on 32bit :)

---

### Post by NightwishFan on 2010-05-03
That is not how Linux manages memory. Free is not free. A main advantage of 64-bit is allocating large ram fast.
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by MeanEYE on 2010-05-04
Lol... Now I turned :D to newbie... hahah thanx :) didn't know that actually :)

---

