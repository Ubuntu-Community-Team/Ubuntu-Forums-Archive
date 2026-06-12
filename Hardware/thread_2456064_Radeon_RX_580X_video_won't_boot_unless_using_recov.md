---
title: "Radeon RX 580X video won't boot unless using recovery mode"
date: 2021-01-03
forum: Hardware
---

### Post by phrankhs on 2021-01-03
Ubunto 20.04.1 LTS

I think it's the AMD Radeon graphics card driver because it only boots using the standard linux drivers and my Laptop, which has an nVidia graphics "card" works perfectly

Update 1/11/21

Now my laptop won't boot with the nVidia driver

My desktop is my gaming system so I would like to use the best drivers, my laptop's nVidia graphics isn't as important

---

### Post by CelticWarrior on 2021-01-03
Welcome.

The AMD graphics drivers that are installed by default in any Ubuntu are the standard. No user action needed.
Have you tried to install something else? If so, what was that?

---

### Post by Yellow Pasque on 2021-01-04
If possible, try a LiveUSB of 20.10. If that works, you may want try a newer kernel in your 20.04 install:
```
sudo apt-get install linux-generic-hwe-20.04-edge
```

---

