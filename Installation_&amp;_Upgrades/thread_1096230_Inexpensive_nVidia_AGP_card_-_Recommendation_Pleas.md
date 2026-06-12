---
title: "Inexpensive nVidia AGP card - Recommendation Please"
date: 2009-03-14
forum: Installation &amp; Upgrades
---

### Post by crjackson on 2009-03-14
A friend of mine shipped me his old tower for some upgrades. The motherboard is not on the list. Currently it's running an AthlonXP 2600 with 512MB and it's pretty peppy except for the old Trident xp/Blade 16mb video card. If fact, ubuntu Hardy has some issues with it - static on the screen.

So anyway, this Shuttle AK322 motherboard has an AGP slot for video and I need to find an inexpensive nVidia card that can handle desktop effects under Jaunty when it comes out.

I'm reading some negative things about the fx5500 and the BFG 7800GS - Can someone recommend an AGP card that fits the bill?

Thanks

---

### Post by tommcd on 2009-03-14
> **crjackson said:**
> 
I'm reading some negative things about the fx5500 and the BFG 7800GS - Can someone recommend an AGP card that fits the bill?

Here is the official list of supported nvidia cards:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia)
The 5500 is on the list. The only 7800 series card listed is the 7800GT. I would think that the 7800GS would likely work though.
Run:
```
aptitude show nvidia-glx-180
```
and:
```
aptitude show nvidia-glx-177
```
to see what cards the drivers support. They mostly overlap, as the same cards are supported by both.
I can confirm that the nvidia gforce 5200 and 6200 AGP cards work well in Ubuntu also.

---

### Post by crjackson on 2009-03-14
> **tommcd said:**
> Here is the official list of supported nvidia cards:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia)
The 5500 is on the list. The only 7800 series card listed is the 7800GT. I would think that the 7800GS would likely work though.
Run:
```
aptitude show nvidia-glx-180
```
and:
```
aptitude show nvidia-glx-177
```
to see what cards the drivers support. They mostly overlap, as the same cards are supported by both.
I can confirm that the nvidia gforce 5200 and 6200 AGP cards work well in Ubuntu also.

Sweet.. Thanks, I didn't know you could check like that. Very cool...

---

### Post by crjackson on 2009-03-16
Okay, here's a new spin on the situation and I need some help and advice on this. I've been googleing a lot and still haven't found the answer.

This is an old shuttle AK32L (AK322) MB. The AGP slot is a 4x 3.3v slot. I almost bought the 6200 on ebay and from everything I can find, it wont work with 3.3v boards so I bailed out.

can someone  point me to a good card that will fit the bill?  Thanks again...

---

### Post by tommcd on 2009-03-17
You will have to do searching on Ebay or Amazon. A quick search of newegg.com reveals only 3 AGP video cards. It seems that AGP is all but phased out. I don't think any manufacturers are making them anymore.

---

### Post by crjackson on 2009-03-17
> **tommcd said:**
> You will have to do searching on Ebay or Amazon. A quick search of newegg.com reveals only 3 AGP video cards. It seems that AGP is all but phased out. I don't think any manufacturers are making them anymore.

Thanks for the reply. I have scrapped the idea of upgrading this old board. I have purchased a used Asus 939 board for a foundation to build on. It just made more sense.

---

