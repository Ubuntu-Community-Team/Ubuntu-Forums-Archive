---
title: "Dell 1505 wireless chipset"
date: 2007-06-06
forum: Hardware &amp; Laptops
---

### Post by Glimps on 2007-06-06
I got this new Dell XPS M1210. Great laptop. Thing is, when I bought it, I had a free upgrade to wireless N (dell 1505 chip), which I didn't figure out until I got the laptop.

As you might know, Linus doesn't even detec the hardware. My thought is, Dell surely didn't reinvent their 802.11 a/b/g chip. Maybe there is a driver I could load that would make the b/g protocol work? Thing is I really want to have ubuntu /w my wireless working on this laptop. It comes with Windows Vista, and so far I hate it. It misses a lot a useful features and it's so slow to boot up I have time to make myself a tea before it's done (great reaplcement for the tea timer software on Linux though!).

If there it's not possible to load an alternative driver, do you know if there is a driver for wireless n support under developpment? 

TIA

---

### Post by Hisstareia on 2007-06-07
If its anything like my computer, ndiswrapper might work. See this link for more information: [https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty](https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty)

Note you might have to use another driver from the same package in order to get it to work. Using it is somewhat spotty, but works as a good temporary solution until Pro Wireless AGN linux drivers come out (sometime in the next month or two...hopefully). For me, the newest ndiswrapper version also caused major issues with the card, so I had to roll back to ndiswrapper 1.44. Just a heads-up.

---

