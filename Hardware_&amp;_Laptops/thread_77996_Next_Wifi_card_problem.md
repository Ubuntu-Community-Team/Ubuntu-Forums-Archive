---
title: "Next Wifi card problem"
date: 2005-10-17
forum: Hardware &amp; Laptops
---

### Post by ov3rdose on 2005-10-17
Hello,
My next problem :(
I've got Toshiba laptop and PCMCIA wifi card Planet WL-3563
I ve install ndsiwrapper and I've install win drivers for that card with ndiswrapper and everything was allright (no errors) but the card is offline. I plug that card to laptop and nothing happens. On card there is stand by light and it doesn't on. I don't know where is problem, with my laptop, with Ubuntu......anybody knows? On XP everything was allright long time ago.......

---

### Post by Dr. Nick on 2005-10-17
Does the card show up under "system - administration - networking" ubuntu doesnt auto connect to an AP like XP does, so it may be working just not set up fully

---

### Post by ov3rdose on 2005-10-18
Ok, but the problem is with power I think. The card isn't ON and I don't know what is wrong, system, card, laptop......

---

### Post by FLeiXiuS on 2005-10-18
What does ifconfig provide? 

If anything at all, try 
```
sudo ifconfig <interface> up

ex: sudo ifconfig wlan0 up

```

See how that works out for you.

---

