---
title: "About MSI Geforce GTX 1650 Super Display card"
date: 2020-11-28
forum: Hardware
---

### Post by satimis on 2020-11-28
Hi all,

Just purchased MSI Geforce GTX 1650 Super Display card.  It needs a 6 pin power connector.  Where can I find it on the power supply?  Whether I need to purchase a new power supply.

If YES please recommend a model.  Thanks

Regards

---

### Post by CatKiller on 2020-11-28
6-pin connections are often made with a 4-pin connector and supplemental 2-pin connector. If your power supply has labelled connectors they'll likely be labelled as PCIe.

They're a standardised connector, so you shouldn't need a new power supply on that basis. If you need a new power supply because your existing one can't supply enough power, or is not of sufficient quality, my standard recommendation is Seasonic, with fully modular cabling for preference.

---

### Post by satimis on 2020-11-28
> **CatKiller said:**
> 6-pin connections are often made with a 4-pin connector and supplemental 2-pin connector. If your power supply has labelled connectors they'll likely be labelled as PCIe.

They're a standardised connector, so you shouldn't need a new power supply on that basis. If you need a new power supply because your existing one can't supply enough power, or is not of sufficient quality, my standard recommendation is Seasonic, with fully modular cabling for preference.
Thanks for your advice.

There is no connector of my power supple labelled as PCIe connector.  All connectors are for hard disks except those for motherboard.  They can't be plugged into MSI Geforce GTX 1650 Super Display card.

I have the display card installed.  It can't be detected on booting the PC resulting in PC unable to boot up.  The fans of the display card is NOT running.

Any advice?  Thanks

Regards

---

### Post by DuckHook on 2020-11-28
There are cable splitters that can split off additional cables from your power supply to power other devices like video cards. They are cheap and readily available. However, then, the problem becomes:

[list=1]
[*]Can your PSU handle the extra load,
[*]How old (read: reliable and clean) is your PSU,
[*]If the video card draws heavy load, then very occasionally and especially with a poor/cheap splitter, this will cause voltage drop to MOBO which, needless to say, is a very bad thing. Highly unlikely, but bad when it happens.
[/list]
We have no idea what your PSU rating is, what your MOBO's draw is, what your video card's draw is. The math isn't complicated, but only you can do it.

BTW, if a card needs power, then of course it will not work if it has no power. This is no surprise.

Lastly, *do not skimp* on your PSU. My attitude is: make sure you have more than enough power for all components. I plan for at least 50% overcapacity. Overloaded PSUs are some of the most difficult problems to chase down because the resulting behaviour has no rhyme or reason and is almost impossible to trace back to insufficient (or dirty) power.

---

### Post by satimis on 2020-11-28
> **DuckHook said:**
> There are cable splitters that can split off additional cables from your power supply to power other devices like video cards. They are cheap and readily available. However, then, the problem becomes:


Thanks for your advice.

I suppose I need a 2xmolex to PCI-E adaptors (pls see attached photo).  I can purchase it in computer component shops.

> 
[list=1]
[*]Can your PSU handle the extra load,
[*]How old (read: reliable and clean) is your PSU,
[*]If the video card draws heavy load, then very occasionally and especially with a poor/cheap splitter, this will cause voltage drop to MOBO which, needless to say, is a very bad thing. Highly unlikely, but bad when it happens.
[/list]
We have no idea what your PSU rating is, what your MOBO's draw is, what your video card's draw is. The math isn't complicated, but only you can do it.
My PSU - Corsair CS550M
Continuous power W - 550 Watts

Specification
[https://www.corsair.com/us/en/Categories/Products/Power-Supply-Units/cs-series-config/p/CP-9020076-NA#tab-tech-specs](https://www.corsair.com/us/en/Categories/Products/Power-Supply-Units/cs-series-config/p/CP-9020076-NA#tab-tech-specs)

I still have spare HD cables available

This is a spare PC having been running for >10 years.  I use it to test MSI display card.

I don't do overclocking here.   I only have one WD mechanical HD installed and one DVD ROM. The other 2 are SSD HDs.  Ubuntu 20.04 desktop is running on a 2TB SSD

Other advice noted with thanks

Regards

---

### Post by Yellow Pasque on 2020-11-29
> Corsair CS550M
There is no connector of my power supple labelled as PCIe connector.

^That does not add up. The CS550M has modular connectors for PCI-e from what I see. Look at the pics: [https://www.newegg.com/corsair-cs-series-cs550m-cp-9020076-na-rf-550w/p/N82E16817139184](https://www.newegg.com/corsair-cs-series-cs550m-cp-9020076-na-rf-550w/p/N82E16817139184)
The CS550M should have plenty of power for the GPU (unless your CPU is a giant power hog) and it's a single 12V rail. So, the Molex adapters should work okay, but it would be better if you just looked for the cables that came with the PSU.
Or, you could even buy a replacement PCI-e cable. [https://www.corsair.com/us/en/Categories/Products/Accessories-%7C-Parts/PC-Components/Power-Supplies/Type-3-Sleeved-Black-PCIe-Cable/p/CP-8920111](https://www.corsair.com/us/en/Categories/Products/Accessories-%7C-Parts/PC-Components/Power-Supplies/Type-3-Sleeved-Black-PCIe-Cable/p/CP-8920111)

---

### Post by satimis on 2020-11-29
> **Yellow Pasque said:**
> ^That does not add up. The CS550M has modular connectors for PCI-e from what I see. Look at the pics: [https://www.newegg.com/corsair-cs-series-cs550m-cp-9020076-na-rf-550w/p/N82E16817139184](https://www.newegg.com/corsair-cs-series-cs550m-cp-9020076-na-rf-550w/p/N82E16817139184)

Thanks for your advice.

Your link doesn't work.  It popup```

Sorry
We can't find this Item. Please check your Item#
```

> 
The CS550M should have plenty of power for the GPU (unless your CPU is a giant power hog) and it's a single 12V rail. So, the Molex adapters should work okay, but it would be better if you just looked for the cables that came with the PSU.
Or, you could even buy a replacement PCI-e cable. [https://www.corsair.com/us/en/Categories/Products/Accessories-%7C-Parts/PC-Components/Power-Supplies/Type-3-Sleeved-Black-PCIe-Cable/p/CP-8920111](https://www.corsair.com/us/en/Categories/Products/Accessories-%7C-Parts/PC-Components/Power-Supplies/Type-3-Sleeved-Black-PCIe-Cable/p/CP-8920111)
Just check my Corsair CS550M PSU.  There is no spare socket for Type 3 Sleeved Black PCIe Cable.  I think I should get the Molex adapters.

Regards

---

### Post by Yellow Pasque on 2020-11-29
> **satimis said:**
> Your link doesn't work.

*Shrug* Works for me...

> Just check my Corsair CS550M PSU.  There is no spare socket for Type 3 Sleeved Black PCIe Cable.  I think I should get the Molex adapters.

Either there are multiple models named CS550M or you're not looking at it correctly. Here's a pic. See how it says 6+2 PCI-E?
Again, find the cables that came with your PSU. If that's too hard, then throw away a few bucks on Molex adapter(s). It's your money.

---

### Post by satimis on 2020-11-30
> **Yellow Pasque said:**
> 
.......
Either there are multiple models named CS550M or you're not looking at it correctly. Here's a pic. See how it says 6+2 PCI-E?
Again, find the cables that came with your PSU. If that's too hard, then throw away a few bucks on Molex adapter(s). It's your money.
Hi,

I got it.  The socket was covered by cables.  I removed the PSU out from PC case for cleaning and found it.  Also I found the PCIe cable in its packing box, still sealed inside a plastic bag.

Now I have the display card installed and connected to power supply.  Then it works.

$ xrandr
```

Screen 0: minimum 320 x 200, current 3840 x 2160, maximum 16384 x 16384
DP-1 connected primary 3840x2160+0+0 (normal left inverted right x axis y axis) 697mm x 392mm
3840x2160 60.00*+ 59.97 29.98
3200x1800 59.96 59.94
2880x1620 59.96 59.97
2560x1600 59.99 59.97
2560x1440 59.99 59.96 59.95
2048x1536 75.00 60.00
1920x1440 75.00 60.00
......
......
.....

```


"Screen 0: minimum 320 x 200, current 3840 x 2160, maximum 16384 x 16384"
**"maximum 16384 x 16384"** I suppose this Display Card can support 8K display

Thanks for your help.

Regards

---

### Post by Yellow Pasque on 2020-11-30
Great! Please mark thread Solved (Thread Tools menu above first post).

---

### Post by satimis on 2020-11-30
> **Yellow Pasque said:**
> Great! Please mark thread Solved (Thread Tools menu above first post).
Still having problem after installing the display card.  At booting it popup "Booting order not found"

On BIOS
Booting
1st Boot```

UEFI OS Samsung SSD 860 EVO 2TB

```

It can't be saved

On next boot it selects```

Ubuntu SSD 860 EVO 2TB

```

Where I have to fix this problem.

Thanks

Regards

---

### Post by CelticWarrior on 2020-11-30
That is an entirely different problem worth of its own thread.
You may reference your journey with a link to this one if you want even if irrelevant (it is).

---

### Post by satimis on 2020-11-30
OK I'll start another thread

---

