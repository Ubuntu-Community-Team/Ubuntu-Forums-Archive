---
title: "Where is my 10MHz/20MHz? (factory overclocked gpu)"
date: 2011-12-01
forum: Hardware
---

### Post by pqwoerituytrueiwoq on 2011-12-01
I just got my self a [ASUS ENGTX550 TI DC/DI/1GD5]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814121435") it is factory over clocked about 1.1% i thought the clock speeds was in the bios/firmware of the gpu so where is it
my gpu clock speed and processor clock speeds on the gpu are at the stock nvidia speeds for the chip-set
i have not checked the core speeds on windows all i did was take my gt 430 out and put the 550 ti in (and connect the added power cable)

it is not a big deal i just want to know why i am not seeing the factory overclock that was advertised on the product even at stock speeds this chip has plenty of overkill for me

---

### Post by searchfgold6789 on 2011-12-01
Overclocking is a funny thing. Are you doing a literal benchmark in Linux, or are you just checking system information provided by typical means, for example lshw or some other hardware lister?
The difference is this. While a benchmark of the hardware will probably return the expected increase in clock speed, unless Newegg is cheating you which is unlikely, the piece of hardware itself has circuits built into it that tell the rest of the computer how fast it was *made* to be.
Windows will probably tell you the same thing a standard hardware-listing Linux program will.
In other words, there's a difference between extracting the clock speed information from the chip, and actually testing to see how fast the clock is, and that's the same difference between looking at System Information and running a literal benchmark.
I hope I have clarified a bit.
 - search

---

### Post by pqwoerituytrueiwoq on 2011-12-01
i looked in nvidia settings atm it is at 50Mhz for power save (variable setting)
but it only goes up to 900 not the 910 advertised on the gpu
to my understanding the driver is not responsible for the clock speeds on the gpu which voids the only logical explanation for what i am seeing
would rather not use windows to check if it gets 910 since that thing annoys me to no end (the poor window management and the start menu)

---

### Post by pqwoerituytrueiwoq on 2011-12-02
does it count as factory overcooked if you have to update the bios on it to get the over clock?
edit:
why does ubuntu say it is a pci-e 1.0 when windows sys it is a 2.0?
edit it switches to 2.0 under load

---

### Post by mörgæs on 2011-12-02
Moved to Hardware & Laptops.

---

### Post by searchfgold6789 on 2011-12-02
Okay, the tool you're using to measure the clock speed will be inaccurate because it interacts with a different part of the actual piece of hardware - perhaps a different part of the GPU chip itself - than what actually runs. If you've ever seen an overclocked GPU (or CPU) then you'll notice all it has is a couple components soldered to it that make the clock itself run faster. If the actual default speed of the GPU was altered, the other components on the GPU card would have to be changed to allow for that. That's why it's called Overclocking instead of Chip Speed Augmentation or something.

---

### Post by pqwoerituytrueiwoq on 2011-12-02
i updated the bios/firmware on it and now it have the factory overclock that was advertised

---

