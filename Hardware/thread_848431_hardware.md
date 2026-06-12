---
title: "hardware?"
date: 2008-07-03
forum: Hardware
---

### Post by downset13 on 2008-07-03
I was wondering how exactly one goes about checking to see what hardware
they have in their computer (specifically the graphcis card) in ubuntu.  I'm trying to dual boot windows but windows never finds my gfx card driver so i don't know exactly what I'm running, lol.

Thanks!

---

### Post by Marshal0505 on 2008-07-03
lshw - list hardware
type 
```
man lshw
```
for more info

---

### Post by downset13 on 2008-07-03
sweet... it worked in every category but one:

the graphics card... it just lists it as a standard vga compatable card

I need some way of finding out the model number.
I know it's an nvidia geforce go...but other than that

---

### Post by estyles on 2008-07-03
Best way I can think of is to open up the computer, write down any promising-looking numbers off the gfx card, and then look it up on nvidia.

I have an ATI Radeon card, and it's basically one driver that runs all kinds of Radeon cards, so even though I eventually remembered that I had an X800, when installing in windows, I just had to install the standard Radeon driver.  Not sure if that's true with nVidia - haven't used their cards in probably 10 years.

---

### Post by Marshal0505 on 2008-07-03
sorry was out doing other stuff :)
try ```
lspci | grep VGA
```

---

