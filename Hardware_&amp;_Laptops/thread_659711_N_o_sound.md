---
title: "N o sound?"
date: 2008-01-06
forum: Hardware &amp; Laptops
---

### Post by Avant Gardener on 2008-01-06
When I tried listening to a video in the examples folder on the LiveCD, there was no sound. Is this a problem with my speakers, or am I missing a driver or something?

I checked the cd after I rebooted, and the Ubuntu scanner-checker-thingy said there were no errors.

---

### Post by eggdeng on 2008-01-07
Post the output of ```
aplay -l
``` If there is no output, try to identify your sound card using ```
lspci
```

---

### Post by NilsE on 2008-01-07
You can also try this:

In a terminal run: asoundconf list

This should return a list of cards.

Replace   xxxxx  below with the name you found in list. I believe it is case sensitive.

In a terminal run: asoundconf set-default-card xxxxxx

Then again with sudo: sudo asoundconf set-default-card xxxxx
 
This will set the defaults for both user and root to the default card and create a config file.

---

### Post by Danyl on 2008-01-07
NilsE, I've just spent hours trying to get my Gigabye USB speakers to play flash sound and your solution was the only one that worked!

Thank you so much!

---

### Post by NilsE on 2008-01-07
> **Danyl said:**
> NilsE, I've just spent hours trying to get my Gigabye USB speakers to play flash sound and your solution was the only one that worked!

Thank you so much!
Great.  Appreciate the feedback.

---

