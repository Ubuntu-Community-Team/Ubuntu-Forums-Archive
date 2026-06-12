---
title: "No sound; help please"
date: 2007-04-15
forum: Hardware &amp; Laptops
---

### Post by Chappy7777 on 2007-04-15
I am getting no sound from my PC. I have an old P2-500 (overclocked) with 768 mgs sdram. The soundcard worked the last time I tried it on an XP PC (same PC, different HDD). It is an old ISA slot Creative Labs SB16. One of their older models, since I've had the card since 1995 or so. It's a huge card compared to today's PCI cards. 

Anyone have any ideas? I'm really new at Linux, so going out and finding drivers for this card, downloading and installing them would be a real challenge for where I'm at. I would have thought Ubuntu might have the drivers for this card built into the OS (6.06).

Thnx,

Chappy

---

### Post by lapsey on 2007-04-15
There is a fairly good guide at [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449).

However, It doesn't cover the Audigy 'Analog/Digital Output Jack' issue, though. Try running 'Gmix' (or 'Kmix' if you are using KDE) , going to the 'Switches' tab and unchecking the option (Audigy Analog/Digital Output Jack) there. **This may well be the issue since they are both Creative Labs cards.**

Also:

> **TheJF said:**
> I'm not sure which of these did it for me, but you can try those:

```
sudo asoundconf list
```

From there, you grab the name of your card, for me it was nForce2

```
sudo asoundconf set-default-card nForce2
sudo asoundconf reset-default-card
```

And then, just for good measures:
```
sudo asoundconf set-default-card nForce2
```

---

