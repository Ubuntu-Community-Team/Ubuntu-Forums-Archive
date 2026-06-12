---
title: "burt out GPU fan"
date: 2010-12-01
forum: Hardware
---

### Post by gamebusterzade on 2010-12-01
after noting that my GPU was was running hot i desided to see if the fan was working
it wasn't 

dose any one know how to fix/replace it cheaply 

or am i freak worrying about this

---

### Post by Decatf on 2010-12-01
Replace it otherwise your graphics card will burn out. There are lots of graphics card coolers available. You just need to find one that is compatible with what you have.

---

### Post by gamebusterzade on 2010-12-01
well that is what i figured 

i guess i will have go find a new one when that one burns out (i hope that is not for some time for it is a good nivida card)  

i will be tiring to fix it for free with what i have(that is what i payed for the whole rig i wont feel to guilty braking it) 

still i hope this works 

i will be open for any comments on how to do this

to every one that posts

THANK    :wink:

---

### Post by mastablasta on 2010-12-02
first thing to do would be to tell us what card you have.

---

### Post by cascade9 on 2010-12-02
> **gamebusterzade said:**
> i will be tiring to fix it for free with what i have(that is what i payed for the whole rig i wont feel to guilty braking it) 

still i hope this works 

It might be possible to fix the fan with a bit of oil, depending on how its broken (you remove the sticker on top of the fan, put a drop of oil into the bearings, then stick the sticker back down).

---

### Post by gamebusterzade on 2010-12-02
> **cascade9 said:**
> It might be possible to fix the fan with a bit of oil, depending on how its broken (you remove the sticker on top of the fan, put a drop of oil into the bearings, then stick the sticker back down).
  

that might work if there was a sticker on top but i can pull the fan apart and force it in from the bottom(there is no way in from the top)

---

### Post by gamebusterzade on 2010-12-02
> **mastablasta said:**
> first thing to do would be to tell us what card you have.
   i would tell u if i know where to find all that info

Later i will try and look up the serial number if i find time (it would help if i was sure it is a nividia card)

---

### Post by cascade9 on 2010-12-02
> **gamebusterzade said:**
> i would tell u if i know where to find all that info

Later i will try and look up the serial number if i find time (it would help if i was sure it is a nividia card)

No need to look up serial numbers (and you'd have a really _fun_ time finding the serial number anyway). 

sudo lshw

Then just copy the video card information, like this- 

```
*-display
                description: VGA compatible controller
                product: G84 [GeForce 8600 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:18 memory:fa000000-faffffff memory:d0000000-dfffffff memory:f8000000-f9ffffff ioport:ef00(size=128) memory:fb000000-fb01ffff

```

---

### Post by gamebusterzade on 2010-12-03
i will try this but it going to be a few days

if there are any other thoughts on this please speak up

---

### Post by gamebusterzade on 2010-12-03
if u noted in the past i said it was free 

that and it is a few years old 

so unless they have a really good warranty there is no chance of having one

---

### Post by steve7777777 on 2010-12-03
No on board video or can't you borrow an old video card untill you get it fixed, or maybe get a card off of Ebay and resell it once you get the fan issue sorted out?

---

### Post by gamebusterzade on 2010-12-03
yes there is an on board video spot

that will be what i will be using after i get all the info on what it is

---

### Post by gamebusterzade on 2010-12-08
> **mastablasta said:**
> first thing to do would be to tell us what card you have.


nividia geforce fx 5200

---

### Post by cascade9 on 2010-12-08
> **gamebusterzade said:**
> nividia geforce fx 5200

All the FX5200s I've seen use cheap 'northbridge' style coolers. I've run one with a passive northbridge cooler and had no porblems, but the case I ran it in had pretty good airfow. If you tried it in a case with bad airflow it would overheat.

---

### Post by gamebusterzade on 2010-12-09
well thanks for the help 

i might have found a cheap northbridge heatsink to replace the fan with 

but can i safely unplug the fan from the GPU board

---

### Post by cascade9 on 2010-12-11
Yes, unplugging the fan from the video card isnt dangerous.

---

### Post by gamebusterzade on 2010-12-16
thank for the help

i should be getting the parts today

---

