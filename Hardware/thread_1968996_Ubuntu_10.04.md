---
title: "Ubuntu 10.04"
date: 2012-04-29
forum: Hardware
---

### Post by deepakdeshp on 2012-04-29
i want to set up a Ubuntu box without monitor and keyboard . The Ubuntu server 10.04 should have 2gb ram, 500 gb hdd an P4 2.8 ghz or more cpu . I am looking for a combination of cheapest cpu and motherboard to cater to the above configuration.

---

### Post by Bandit on 2012-04-29
> **deepakdeshp said:**
> i want to set up a Ubuntu box without monitor and keyboard . The Ubuntu server 10.04 should have 2gb ram, 500 gb hdd an P4 2.8 ghz or more cpu . I am looking for a combination of cheapest cpu and motherboard to cater to the above configuration.

What are you going to be running on the box?

---

### Post by ahallubuntu on 2012-04-29
I don't recommend Ubuntu 10.04 LTS for generic P4 systems because 10.04 had a ton of problems with several Intel integrated graphics chipsets - and you could wind up with weird graphics issues and freezes.  If you are using a dedicated graphics card you should be OK, though.

Otherwise, I would recommend using the new 12.04 LTS instead - much more likely to work better with an old P4.  I put 11.04 on a couple of  P4 boxes and it worked very well.

I'd probably avoid a P4 these days if you can avoid it.  Look for a cheap Pentium Dual Core even if the GHZ is a lot lower.  Don't forget, Intel changed CPU architectures after P4 so the clock rates dropped but performance was about the same - so a 2.8GHZ P4 is about as fast as 1.6GHZ Core 2 Duo even with just one core running.  Pentium Dual Core is a good budget version of the Core 2 Duo but a far better CPU than P4.  It runs much cooler for one thing.

---

### Post by deepakdeshp on 2012-04-30
> **ahallubuntu said:**
> I don't recommend Ubuntu 10.04 LTS for generic P4 systems because 10.04 had a ton of problems with several Intel integrated graphics chipsets - and you could wind up with weird graphics issues and freezes.  If you are using a dedicated graphics card you should be OK, though.

Otherwise, I would recommend using the new 12.04 LTS instead - much more likely to work better with an old P4.  I put 11.04 on a couple of  P4 boxes and it worked very well.

I'd probably avoid a P4 these days if you can avoid it.  Look for a cheap Pentium Dual Core even if the GHZ is a lot lower.  Don't forget, Intel changed CPU architectures after P4 so the clock rates dropped but performance was about the same - so a 2.8GHZ P4 is about as fast as 1.6GHZ Core 2 Duo even with just one core running.  Pentium Dual Core is a good budget version of the Core 2 Duo but a far better CPU than P4.  It runs much cooler for one thing.


I am not running any graphics as it is a server and will work on command mode.

I already have set up the server with Ubuntu10.04 and I dont want to do a fresh install of Ubuntu 12.04 hence I will try upgrading to version 12.04

I am ok with even AMD processors. They run fine and are more powerful at they same price. Let me check the price diff between 2.8 ghz p4 and core 2 duo 1.6 Ghz. Thanks for the update.

---

