---
title: "Need Info 8600GTS G84 chip specs"
date: 2008-06-15
forum: Hardware
---

### Post by Samurai Penguin on 2008-06-15
I just got a MSI 8600GTS card that came with a real nice cooler with dual power connectors for the fan - one for normal rotation and the other for slower rotation. Naturally, when I plugged in the lower rpm connector, I did it incorrectly and I fried the fan.

So I rigged up an external fan to blow on the cooler and it seems to be working quite well. Question is, what is the maximum safe operating temp for a 8600GTS G84 chip? I didn't record the operating temp before the fan fried so I have no reference to know if the G84 chip is now running hot or not. I searched the net but could not find even one max temp spec (not meven at Nvidia website).  Thanks

---

### Post by sdennie on 2008-06-15
I would try nvidia-settings.  Just type "nvidia-settings" in a terminal.  If it's not installed you'll get instructions on how to install it.  From there, you should see a Thermal Monitor selection on the left side.  Many cards will display a "Slowdown Threshold" that is essentially the point where the card is so hot that it underclocks itself.

---

