---
title: "Hardware change"
date: 2007-06-24
forum: Hardware &amp; Laptops
---

### Post by lennartack on 2007-06-24
Hello,
I bought some new hardware for my pc and don't want to reinstall ubuntu. Can I just keep using my current installation(with some modifications maybe?), or move the settings of my current installation to a new installation? New hardware:
- Motherboard
- Processor(from amd sempron to pentium 4)
- More ram

I still use the same graphics card and sound card.


Thanks!

Lennart

---

### Post by ukripper on 2007-06-24
You have changed major components of your machine. You do need to reinstall your ubuntu to detect those changes and correct drivers for your new components.
Before you do reinstallation just backup up your data and home drive and then reinstall ubuntu, after new installation restore your backed up data.

---

### Post by joe.turion64x2 on 2007-06-24
> - Processor(from amd sempron to pentium 4)
I can not imagine an upgrade from Sempron to Pentium 4, a downgrade perhaps (unless it is a very latest P4 HT). 
It is a good practice to have a separate /home partition so when you reinstall you only have to format /. Several years ago I did this with Mandriva: upgraded from Mandrake 10 to Mandriva 2006, just left alone the /home partition (no format for it), mounted it, added the same user names and when I logged in I was even greeted by my old settings.

Joe.

---

### Post by ukripper on 2007-06-24
It is always the best practice to have your /home partion seperate as Joe described in situations like this but nevermind if you still don have home seperated you just backup your data and /home drive and restore once ubuntu is installed.

---

### Post by joe.turion64x2 on 2007-06-24
> **ukripper said:**
> It is always the best practice to have your /home partion seperate as Joe described in situations like this but nevermind if you still don have home seperated you just backup your data and /home drive and restore once ubuntu is installed.
In fact I found it the best practice for me (only user) to have a big Linux partition (no home) for storage purposes and mount it under the /home directory. That way, if you like multibooting other Linuxes you can mount it as well and easily access your data. Besides it provides the same advantages of a separate /home when reinstalling.

Joe.

---

### Post by lennartack on 2007-06-25
> **joe.turion64x2 said:**
> I can not imagine an upgrade from Sempron to Pentium 4, a downgrade perhaps (unless it is a very latest P4 HT). 
It is a good practice to have a separate /home partition so when you reinstall you only have to format /. Several years ago I did this with Mandriva: upgraded from Mandrake 10 to Mandriva 2006, just left alone the /home partition (no format for it), mounted it, added the same user names and when I logged in I was even greeted by my old settings.

Joe.
I hope it's not a downgrade. It's an old sempron and a 3GHZ P4 HT, and I can remember that when I bought the sempron this P4 costed something like twice as the sempron costed.

Anyway, I already had a separate home drive, and migration went succesfully :D. Thank you guys!

---

### Post by ukripper on 2007-06-25
Sempron has less L2 cache than Pentium 4, it is similar to celeron processors but bit more cache than celerons. If your Sempron runs at 2 Ghz which would effectively give you performance equal to Pentium 4 1.5Ghz.

i own Sempron, Celeron, Pentium4, AthlonXP and dual core. I found my Sempron faster than celeron although Celeron is 3Ghz and sempron 2.5Ghz

---

### Post by joe.turion64x2 on 2007-06-25
> **ukripper said:**
> Sempron has less L2 cache than Pentium 4, it is similar to celeron processors but bit more cache than celerons. If your Sempron runs at 2 Ghz which would effectively give you performance equal to Pentium 4 1.5Ghz.

i own Sempron, Celeron, Pentium4, AthlonXP and dual core. I found my Sempron faster than celeron although Celeron is 3Ghz and sempron 2.5Ghz
If you are talking about a socket A Sempron then almost all P4 outperform it. However if you are talking about a socket 754 Sempron then the pictures can change depending on the specific model. For example I find my Sempron 3100+ (the first 754 model) at 1.8GHz faster than my school's 2.66GHz P4 HT (same amount of RAM).

Anyway, talking about performance/Watt the Sempron wins.

Joe.

---

