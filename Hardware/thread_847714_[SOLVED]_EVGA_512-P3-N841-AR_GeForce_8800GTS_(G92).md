---
title: "[SOLVED] EVGA 512-P3-N841-AR GeForce 8800GTS (G92)"
date: 2008-07-02
forum: Hardware
---

### Post by VexVishnu on 2008-07-02
I wanted to upgrade my video card to this one, but my friend had A LOT of trouble trying to get the drivers, for his new video card, to work in Ubuntu. (We aren't getting the same video card) I was wondering if anyone knows if there are linux drivers for this one or if they had a better suggestion as to what video cards run well in Ubuntu. Money is no problem, I'm just looking for an uber vid. card.

---

### Post by phidia on 2008-07-02
Generally speaking nvidia cards work very well in linux. There can always be exceptions though.
From the thread [here]("http://ubuntuforums.org/showthread.php?t=221313&highlight=GeForce+8800GTS") there is [one hit]("http://ubuntuforums.org/search.php?searchid=43977137") for that card so someone appears to be using it.

---

### Post by VexVishnu on 2008-07-03
Cool, thanks.

---

### Post by dabl on 2008-07-03
8800GTS works fine. Mine is an EVGA, but 320MB memory -- a different part number.

Use EnvyNG to install the driver, in text mode (in console) and just leave the "Restricted Driver Manager" shut.  

```
sudo apt-get install envyng-core
```

and 

```
sudo envyng -t
```

Are all you need to remember.  ;-)

---

### Post by VexVishnu on 2008-07-03
Thanks to you too!

---

