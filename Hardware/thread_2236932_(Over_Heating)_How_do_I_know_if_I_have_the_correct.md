---
title: "(Over Heating) How do I know if I have the correct drivers and hardware recognition?"
date: 2014-07-29
forum: Hardware
---

### Post by Robert_Hubbard on 2014-07-29
I am a total noob but I am a computer science major and this interests me.  Basically I am having a few problems:

Laptop Details:
     * ASUS Q501L
     * Video Chipset: Intel HD Graphics 4000
 
The issues I'm having:  
     * Fans are running too much (my laptop is hot)
     * Laptop is hot
     * I can not stream in HD
     * Battery life is bad ( I'm assuming because something is working too hard, causing overheating and fans to kick on )

I notice all this when my brightness is on more than (estimate) 15 percent.

Under system settings -> details -> graphics --- it says:
     * Driver: Intel Haswell Mobile
     * Experience: Standard

Does this mean that my display will be standard rather than HD?

I want to do anything I can to make this software maximize the hard ware.

I know there are more questions I should be asking but this is what I can provide with the knowledge I have at the moment.

---

### Post by tgalati4 on 2014-07-29
Install *htop* and observe your CPU load.  Perhaps you have a stuck process.

Open a terminal:

```
sudo apt-get install htop
htop
```

---

