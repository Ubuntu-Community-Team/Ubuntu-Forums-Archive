---
title: "How to install proper drivers for video cards"
date: 2012-09-02
forum: Hardware
---

### Post by pyro.xyz on 2012-09-02
Hello, peoples.

I have been running Ubuntu off and on for a couple of years now (still love it), and I realized that I might not be running the proper drivers for my video card. Then, I realized that I don't even know what video card I even have. Would anyone be able to direct me to how to find my video card type, and the correct drivers? (I peeled the stickers on my laptop off because they looked tacky.)

---

### Post by lordievader on 2012-09-02
To find out what graphics card you have run the following:
```
sudo lshw|less
```
Then look for "*display" (at least that is where my GFX card is noted), or something similar pointing to a GFX card.

---

