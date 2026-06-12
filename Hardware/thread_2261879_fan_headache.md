---
title: "fan headache"
date: 2015-01-21
forum: Hardware
---

### Post by ben_amor on 2015-01-21
i'm new on unbuntu ! just when i put a video the fan start making so much noise :D what's that ????? :/

---

### Post by newbie-user on 2015-01-21
That's probably because your processor is working harder to play the video and generating more heat. Not really an Ubuntu issue, just a heat issue. Make sure the fan is free of dust and that there is ample ventilation in your computer case to let out the heat.

---

### Post by oldos2er on 2015-01-21
Moved to Hardware.

---

### Post by oldrocker99 on 2015-01-21
Also, you might look at the fans and heatsinks in your PC for dust pileup; it can certainly make fans get noisier. Either use a blower on the dust, or, if you're careful, the nozzle of a vacuum cleaner to suck it all away.

---

### Post by Yellow Pasque on 2015-01-22
That's expected behavior, but if watching video doesn't cause as much noise on other OS's, then you may not have video decode acceleration working, and the CPU is doing the heavy lifting. Of course, you need to give more info for anyone to determine that...
Start by giving basic hardware info from lspci:
```
sudo update-pciids
lspci -k
```

---

### Post by ben_amor on 2015-01-22
when i was on windows the fan doesn't make noise when i watch a video except when i lunch games ! i have dell inspiron 3521 and i think this laptop causes many problems ! anyway this is the pc's configuration :
-intel i3 processor
-4gb ram
-amd radeon HD7600 series

---

