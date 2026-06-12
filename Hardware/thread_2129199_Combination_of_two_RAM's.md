---
title: "Combination of two RAM's"
date: 2013-03-25
forum: Hardware
---

### Post by hyperAura on 2013-03-25
Hi,

I have 2 pairs of RAM which I bought in order to setup a new machine but they are incompatible. In order not to waste them, I decided to install one pair to my existing machine but I don't know which combination with existing is the best.

My existing machine has the following motherboard: **Gigabyte **[COLOR=#006FFD][FONT=Arial]**GA-P67A-UD4-B3**[/FONT][/COLOR]

[HTML]http://www.gigabyte.com/products/product-page.aspx?pid=3759#ov[/HTML]

with the following RAM already installed:** Corsair Vengeance 8GB - [COLOR=#363636][FONT=arial]CMZ8GX3M2A1600C8[/FONT][/COLOR]**

[HTML]http://www.corsair.com/vengeance-8gb-dual-channel-ddr3-memory-kit-cmz8gx3m2a1600c8.html[/HTML]


The two pairs of RAM that I have available are the following:

1) **Corsair XMS3 8GB**
[HTML]http://www.corsair.com/cmx8gx3m2a1333c9.html[/HTML]

2) **Corsair XMS3 4GB**
[HTML]http://www.corsair.com/cmx4gx3m2a1600c9.html[/HTML]

So which pair would it be better to install?

Thanks

---

### Post by tgalati4 on 2013-03-25
Memtest would help determine which RAM combination works best.  You will get the speed of the RAM and the reliability by running through a complete pass.  If your BIOS allows, try overclocking the RAM, you may get a 10% speed improvement.  One set of RAM may overclock better than another.

---

### Post by Yellow Pasque on 2013-03-25
4GB kit: DDR3-1600, 9-9-9-24, 1.65V
8GB kit: DDR3-1333, 9-9-9-24, 1.5V

The 4GB kit is faster, so unless you're doing something that requires more than 4GB, it's a no-brainer in my book. Yesterday, I had two VM's (each allocated 1GB of memory), my music player, 5-6 tabs in Firefox, and some other stuff running, and I was still only using about 3GB of the 4GB I have.

---

### Post by hyperAura on 2013-03-25
Hi Temüjin,

I tried installing the 8GB and I checked in the BIOS it says that speed is down to 1333 so you were right. What I don't understand however is that instead of recognizing 16GB's of RAM it says that I have only 14GB. What might be the reason for this?

Thanks

> **Temüjin said:**
> 4GB kit: DDR3-1600, 9-9-9-24, 1.65V
8GB kit: DDR3-1333, 9-9-9-24, 1.5V

The 4GB kit is faster, so unless you're doing something that requires more than 4GB, it's a no-brainer in my book. Yesterday, I had two VM's (each allocated 1GB of memory), my music player, 5-6 tabs in Firefox, and some other stuff running, and I was still only using about 3GB of the 4GB I have.

---

### Post by Yellow Pasque on 2013-03-25
> **hyperAura said:**
> I tried installing the 8GB and I checked in the BIOS it says that speed is down to 1333 so you were right.
You could try bumping the RAM voltage to 1.65V, and OC'ing it to DDR3-1600 (and then check for stability with Memtest). I'm guessing it would work, but personally, I would rather have peace of mind running my RAM at the rated speed than getting the small performance boost from OC'ing the RAM. It would be different if we were still in the Pentium4 days and RAM bandwidth was a major bottleneck.

> What I don't understand however is that instead of recognizing 16GB's of RAM it says that I have only 14GB.
Where are you seeing this? BIOS? In Ubuntu? Is your BIOS updated?

---

### Post by tgalati4 on 2013-03-25
I have discovered that motherboard chipsets have limitations.  Sometimes when you maximize the RAM on the system, it will declock the RAM.  4GB may run faster than 8GB.  Also, some chipsets run out of address space to keep track of RAM chips, so you may not be able to see all of the RAM depending on how dense the memory chips are that make up the RAM stick.  Only researching and testing your chipset will reveal these limitations.

According to this link:  [http://www.gigabyte.us/products/product-page.aspx?pid=3759](http://www.gigabyte.us/products/product-page.aspx?pid=3759)

You are running an Intel P67 chipset.

A google search on "Intel P67 chipset limitation" produces this result:

Quote:
*4×240pin Note: 1. Before you install memory module on this motherboard, please read below message to avoid any improper installation: - Due to chipset limitation, if you plan to install three or four memory modules on this motherboard, please install only single-sided memory modules. - To install two memory modules on this motherboard, please install them on DDR3_A1 and DDR3_B1 DIMM sockets. 2. For the detailed installation information, please refer to the user manual or quick installation guid*e.

I think what this is saying is that if you have chips on both sides of the RAM stick, then you can't install in all 4 slots.  My interpretation is that the chipset can't handle 4 banks of double-sided chips, therefore it won't see all of the RAM in this situation.  I'm not a RAM expert, but I do know that Intel chipsets have limitations that can bite you.

---

### Post by hyperAura on 2013-03-26
I installed the 4GB pair in order to take advantage of the clock speed (1600), however instead of having clock speed of 1600, in the BIOS the speed is around 1330 and I cannot change it. Using motherboard utilities in Windows I checked whether I can change the clock speed but it was not possible as the clock speed field is not edible.

What might be the reason for this? Is there anything I can do to change the clock speed?

Thanks

---

### Post by tgalati4 on 2013-03-26
As I said, Intel chipsets have limitations.  You just discovered another one.

---

### Post by hyperAura on 2013-03-27
I see. Thanks both of you for helping me out on this.

---

