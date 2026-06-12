---
title: "How To Cut Heat &amp; Fan Noise Via GPU Choice in Hybrid Laptop?"
date: 2013-08-23
forum: Hardware
---

### Post by buzzingrobot on 2013-08-23
I have a new ThinkPad W530, but this question seems relevant to other hybrid laptops:

The BIOS gives me three choices for handling the display:

1. The onboard Intel GPU
2. The discrete Nvidia card
3. Optimus

I'll use this machine for photo editing and processing.  I also don't like noisy machines so I want to reduce fan noise to a safe minimum.

Forgetting the photo work for a moment, which of those three options will generate the least heat and, presumably, trigger the fans less frequently, when used for routine mail, browsing, etc.?

Then, of course, assuming the photo work amounts to "graphics intensive", which choice should I make?

Optimus would require Bumblebee.  Am I correct that Bumblebee does not automatically handle the switching, that "graphics intensive" apps need to be launched manually?

---

### Post by tgalati4 on 2013-08-23
The easiest way to eliminate fan noise is to get a computer without a fan, such as a macbook air.  

Install *thinkfan* and set the thermal limits carefully.  Because the CPU and GPU share the heat sink and the fan cools both, it doesn't really matter which you choose because ultimately it is the workload that will determine the total head load.  The graphics responsiveness and screen artifacts that you see when editing photos will quickly narrow down your graphics choice.

Intel graphic chips tend to run cooler than nVidia, but your lap will  be your guide.

---

### Post by buzzingrobot on 2013-08-23
> **tgalati4 said:**
> The easiest way to eliminate fan noise is to get a computer without a fan, such as a macbook air. [\quote]

Unlikely to do that since I just bought the ThinkPad. ;)

And the Air doesn't have the capacity I want. (I just sold a Macbook Pro.)

[quote]Install *thinkfan* and set the thermal limits carefully.

How is "carefully" done? Check the specs for the machine and keep the temps below whatever Lenovo says is the danger point?

---

### Post by Yellow Pasque on 2013-08-23
The Intel chip will use less power, so I would choose Optimus and try bumblebee. That will give you the option to run apps on the nvidia GPU.


> Am I correct that Bumblebee does not automatically handle the switching, that "graphics intensive" apps need to be launched manually? 
Yes

---

### Post by tgalati4 on 2013-08-23
Lenovo has done careful engineering and the default fan RPM's are needed to remove the heat load.  Anything less will mean that the chips will run hotter.  Many thinkpads have had problems with GPU's delaminating due to heat warpage.  I have a T43p with an ATI FireGL chip and I have my *thinkfan* limits set conservatively because a laptop with a bad GPU is no longer a laptop.

---

