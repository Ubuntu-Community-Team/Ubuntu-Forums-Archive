---
title: "Problem #9,037: Synaptic headers linux 2.6.28.12 make X crash"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by blackSP on 2009-05-06
I just ran a Synaptic update and accepted the latest Linux Headers 2.6.28.12

Booting now results in the famous black screen with the garbled bar at the top. So beware!

Config: Janunty, Asus f8p, Radeon hd2400, ATI 9.4 drivers


Booting with the 2.6.28.11 headers work fine.


Anybody any ideas? I'm getting really frustrated with Jaunty, first time I've seen soooo many problems!, 7.04 through 8.10 were all flawless...

---

### Post by blackSP on 2009-05-07
Bump!

---

### Post by blackSP on 2009-05-07
Bumpy!

---

### Post by blackSP on 2009-05-09
I always thought the Ubuntu community was about helping each other.
But since Jaunty not anymore or much less, so it seems...

Why is that? Because the number of issues is so overwhelming people just don't care anymore? Or is my problem unique? Or irrelevant?

---

### Post by evanrmurphy on 2009-05-09
Sorry to see you've gone so long without a response!

So when you go back to linux-headers-2.6.28-11 and linux-headers-2.6.28-11-generic, X works fine? Or are you unable to try and revert the packages because you can't even boot now? (This part was a little unclear to me.) The new headers haven't caused me any problems so far. :confused:

---

### Post by blackSP on 2009-05-10
Hi, thanks for responding! I went back to the old headers by choosing them during boot-up and X started fine. I tried again with the new headers and presto, bsod. So I removed these headers altogether and now everything is OK.

I googled this issue and haven't found anybody else so far. Strange, I have a common setup so there must be tons of people with this problem...

---

### Post by Wartender on 2009-05-10
this hapens to me too (as i've said in like 4 threads already) but when i booted into the 2.6.27-11 boot, i tried to install the 9.4 catalyst drivers and now that boot is f*cked up too. HELP, i have no other primary boots :(

---

### Post by evanrmurphy on 2009-05-10
> **blackSP said:**
> Hi, thanks for responding! I went back to the old headers by choosing them during boot-up and X started fine. I tried again with the new headers and presto, bsod. So I removed these headers altogether and now everything is OK.

I googled this issue and haven't found anybody else so far. Strange, I have a common setup so there must be tons of people with this problem...

That's very strange. I'm glad you got a stable system back, but it's unsettling the way those headers are reacting with your machine. I wonder if there's a place dedicated to kernel issues (I'm sure there is, I just don't know yet) where a report on this bug would be welcome. I'll let you know if I find it.

> **Wartender said:**
> this hapens to me too (as i've said in like 4 threads already) but when i booted into the 2.6.27-11 boot, i tried to install the 9.4 catalyst drivers and now that boot is f*cked up too. HELP, i have no other primary boots :(

So now you can't boot into X at all?! :( If you do find a way, then it shouldn't be difficult to reinstall the headers. Synaptic handles them like any other package--just search for "linux-headers", and there they are.

---

### Post by evanrmurphy on 2009-05-10
blackSP, have you considered [filing a bug on Launchpad]("https://bugs.launchpad.net/bugs/+filebug")? For the concerned package, they list several linux-headers-2.6, so just select the one specific to your architecture, and then explain the situation as clearly as you did here. (Hardware details will be especially important for this problem, so don't go shy on those.) If you do decide to file, please link to your report from here!

---

### Post by blackSP on 2009-05-11
I have not filed on Launchpad yet but will do so tonight. I wanted to establish first if there are any others with this problem.
I'll post the link here as asap!

---

