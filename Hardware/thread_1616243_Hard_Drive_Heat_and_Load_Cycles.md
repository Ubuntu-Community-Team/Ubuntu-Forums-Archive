---
title: "Hard Drive Heat and Load Cycles"
date: 2010-11-08
forum: Hardware
---

### Post by jutt69 on 2010-11-08
I have an issue with my laptops hard drive since installing Ubuntu 10.10

I noticed the hard drive was getting a lot hotter than it does when running Vista. I have been doing A LOT of reading over the last couple of days to try and figure out what the issue is and find a potential fix.

I have come across lots of forum threads about the load cycle problem people have been facing and have been investigating my own setup. Here's what I have discovered:

When my laptop is plugged in the APM setting defaults to 254 which stops the load cycles increasing too much but allows the heat to rise as high as +60°C.

When I run on battery the APM defaults to 128 which makes the load cycle count increase at a rate of several per minute but keeps the temperature down to a more reasonable 40°C (still hotter than Vista but ok)

Now I know I can change the APM myself but I am unsure what level to go for. Is it better to run at high temperatures or allow the load cycles to increase at what I understand to be an extreme rate?

I have been looking into solid state but don't feel that flush at the moment. Would that help? Would a new "better" Hard Drive help? Really after all the threads I have been trawling I am unsure what to do next.

Thanks in advance for any advice offered.

---

### Post by jutt69 on 2010-11-08
Bump due to edit with better info.

---

### Post by twtduck.ii on 2010-11-08
You may want to consider downgrading to an lts release (probably Ubuntu 1.04). If you want to keep 10.10 try getting better cooling systems and if that doesn't work reinstall 10.10. This is not a good thing to happen to a laptop. Be careful what you choose to buy... I once bought ddr3 ram when my computer runs ddr.

---

### Post by jutt69 on 2010-11-08
Thank you for your response.

I will have a think about going with 10.04 after a bit more research into possible fixes.

I have a heavily partitioned drive, could that be making the problem worse? Worth getting rid of my unused swap partition? (only there to allow hibernate which I could live without)

Also, what effect would the "spin down hard disk" option have? I'm guessing improvement on the temp but worse for load cycles?

---

