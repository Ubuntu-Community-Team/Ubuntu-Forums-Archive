---
title: "Best way to switch a GPU"
date: 2024-01-15
forum: Hardware
---

### Post by demonenero84 on 2024-01-15
I want to change my nvidia gpu (GTX1050) with an amd gpu (Radeon RX 6400).
 Since I do not want to format my hard drive and reinstall kubuntu what would be the best way to proceed ?
thanks a lot in advance

---

### Post by TheFu on 2024-01-15
[LIST=1]
[*]Remove the proprietary drivers and any extra stuff you setup to use those drivers.
[*]Shutdown.
[*]Install the other GPU.
[*]Boot.
[*]Install any proprietary drivers, if any are needed.
[*]Be happy nVidia is out of your box.
[/LIST]

---

### Post by demonenero84 on 2024-01-16
thanks a lot, I will mark this thread solved, if anyone wishes to add any advice I will gladly accept it

---

### Post by TheFu on 2024-01-16
> **demonenero84 said:**
> thanks a lot, I will mark this thread solved, if anyone wishes to add any advice I will gladly accept it

I wouldn't mark it solved until you actually do it.

---

### Post by demonenero84 on 2024-01-16
I guess you are correct, right now I am waiting for the price to drop, I can get a RX 6400 for 130 &#8364; (141,31 $), still rather expensive

---

### Post by deadflowr on 2024-01-16
You might need to remove an xorg.conf fie if nvidia generated one.
I don't know if it still does that or not.
But if one exists it can cause weirdness.
Since the xorg.conf will reference a non-existing card and driver.
It's typically the file /etc/X11/xorg.conf. 
Might also check that the /etc/X11 sub-directories if anything referencing the old card is in anything there, too.

---

### Post by demonenero84 on 2024-01-16
thanks a lot

---

