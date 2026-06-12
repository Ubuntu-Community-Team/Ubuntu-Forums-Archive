---
title: "My laptop crashes running ubuntu"
date: 2008-08-29
forum: Hardware
---

### Post by robincawser on 2008-08-29
I have a Fujitsu-Siemens Amilo D1845 laptop running ubuntu 8.04. Everything works fine, apart from the random crashes where ill have to do a hard restart. Even with a fresh install of ubuntu it will happen, so I'm quite sure its not something i've installed causing it. 
Could you help me troubleshoot my problem?

---

### Post by Crafty Kisses on 2008-08-29
Post the results of this command > top

---

### Post by nicedude on 2008-08-29
I don't know if you will see any misbehaving programs in top and I know in my case I was having thermal shutdowns a while back with mine. Could you try to describe what happens when this happens, can you see any messages on the screen or does screen freeze or go black etc just try to describe as best you can.

---

### Post by robincawser on 2008-09-14
Hi sorry for the late response. I've just reinstalled hardy from a cd and installed all the updates. I've enabled the restricted ATI driver, and I have my visual effects set to normal. Before I had it set to extra with various default plugins enabled. 
So far so good. I've been running it for about a week and not one crash. I tried it on extra again and it did crash within an hour.
Thing is, I would like to have compiz-fusion fully enabled, but I'd also love system stability. 
I'm quite sure its something to do with the ATI driver. Before on past ubuntu installations I've followed other guides on how to install ATI driver, but they all resulted in the same crashes.

---

### Post by robincawser on 2008-09-14
> **nicedude said:**
> I don't know if you will see any misbehaving programs in top and I know in my case I was having thermal shutdowns a while back with mine. Could you try to describe what happens when this happens, can you see any messages on the screen or does screen freeze or go black etc just try to describe as best you can.

when it happens it literally freezes, as in nothing moves on screen, mouse doesnt move, the clock stops.

---

### Post by robincawser on 2008-10-21
bump

It's still happening, albeit less often. I don't have any desktop effects active which seems to have calmed it down a bit.

Please help me get to the bottom of this

---

### Post by dazzled on 2008-10-21
Getting desktop effects to run properly with most ATI cards is problematic to say the least. It's a bit hard to change the card in a laptop, so just turn off all effects.  You have a choice of open source and proprietary graphics drivers - try each and stay with whichever works best - the ATI supplied driver has many Linux conflicts, documented elswhere in the forum

---

### Post by robincawser on 2008-10-21
> **dazzled said:**
> Getting desktop effects to run properly with most ATI cards is problematic to say the least. It's a bit hard to change the card in a laptop, so just turn off all effects.  You have a choice of open source and proprietary graphics drivers - try each and stay with whichever works best - the ATI supplied driver has many Linux conflicts, documented elswhere in the forum

I'm not really fussed about desktop effects, just that they seem to encourage crashing. I've tried the open source drivers a while ago on an old install of ubuntu on this laptop, but that had the same problems as proprietary drivers.

I'm beginning to wonder whether it's nothing to do with my ati chip and to do with something else. Thing is when it was running windows xp, it never crashed like this.

---

### Post by dazzled on 2008-10-21
ATI supplies separate proprietary driver software for both XP and Linux systems to utilise their various graphics chips. Unfortunately the Linux versions of the drivers have many recognised unfixed errors. Most people find it easier not to use these chips with Linux, than to find workarounds for the driver bugs. Sadly it is hard to retrofit a laptop.

There are many online discussions of this problem. Some info is here [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by robincawser on 2008-10-27
bump

---

