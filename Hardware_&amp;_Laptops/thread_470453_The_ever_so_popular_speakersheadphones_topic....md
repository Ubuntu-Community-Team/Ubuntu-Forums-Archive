---
title: "The ever so popular speakers/headphones topic..."
date: 2007-06-11
forum: Hardware &amp; Laptops
---

### Post by pbwalker on 2007-06-11
Toshiba Satellite a135-s4427

So I seem to have the same problem that a lot of people do when it comes to sound playing through the speakers and headphones at the same time. Most topics seem to lean towards ALSA 1.0.14 and I am running that, but still have the same problem. I haven't found a solution that will work.

Sound Card:
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

```
Alsa Version
```
Advanced Linux Sound Architecture Driver Version 1.0.14rc1 (Tue Jan 09 09:56:17 2007 UTC).
```

Another strange thing, unrelated to the issue I think, is when I try to run alsaconf, I get this: ```
-su: alsaconf: command not found
```

Now, the sound works great (after some tweaking). But when I plug in my headphones, sound still comes out of the speakers. I found this out at work, and was the laughing stock for the day! :) 

Any ideas?

---

### Post by Soarer on 2007-06-11
Alsamixer has a 'Head Jack Sense" which 'ought' so fix this, going by the name of it :)

You can install 'alsamixergui' if you want a GUI for it.

---

### Post by pbwalker on 2007-06-11
Well, no luck. When I attempt to make any changes to the headphone volume, it doesn't move. It's stuck at 00. 

Anyone have any other ideas?

---

### Post by pbwalker on 2007-06-11
just thought I'd try a bump...

---

### Post by Maverynthia on 2007-07-05
Having the same problem :/

---

