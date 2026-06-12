---
title: "Toshiba Satellite A100 VA1 Fn key"
date: 2007-03-18
forum: Hardware &amp; Laptops
---

### Post by LactosetheIntolerant on 2007-03-18
I bought a A100 VA1 a few days ago, and have fixed most of the initial problems I had with it(wireless not working, no touchpad scrolling, etc).  I've moved on to trying to make the Fn key do what it's supposed to do but I've run into some problems.  I've read a lot of threads about Toshiba laptops and the Fn key, but none have helped.  fnfx won't work because of the Phoenix bios on the laptop.  

I've checked out the keys with xev, and Fn modifies some keys, but not all.  For example, F3(suspend), F7(restart X), Esc(mute) and the "Numpad" keys are all modified and produce events.  F1, F10 and F11 produce events, but don't do anything.  All other keys that are supposed to be modified by Fn produce no events.

Could this just be a keyboard mapping problem?  Reading other peoples similar problems led me to believe the Fn key shouldn't be working at all.


Running 6.10 Edgy Eft with 2.6.17.11-Generic Kernel.

---

### Post by Chonnawonga on 2007-03-31
I'm experiencing this issue too. Any help?

---

