---
title: "My Home-Built Computer Build: No Hitches?"
date: 2011-02-11
forum: Hardware
---

### Post by TheBritishEditor on 2011-02-11
Hello. I'm building a computer from home, buying parts from Newegg. I need a simple compatibility check to make sure this will work smoothly with Ubuntu. Thanks in advance.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103871](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103871)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16811119233](http://www.newegg.com/Product/Product.aspx?Item=N82E16811119233)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822145299](http://www.newegg.com/Product/Product.aspx?Item=N82E16822145299)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813157200](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157200)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814161315](http://www.newegg.com/Product/Product.aspx?Item=N82E16814161315)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16820220537](http://www.newegg.com/Product/Product.aspx?Item=N82E16820220537)

Keep in mind that I already have a 450 Watt PSU and an optical drive. Thanks.

---

### Post by cascade9 on 2011-02-12
Why a 880/SB710 setup when you are getting avideo card? You would be better off with a 770/870 chipset motherboard. 

BTW, if its an older 450 watt power supply, it could give you problems.

---

### Post by TheBritishEditor on 2011-02-12
Ok. I'm a total noob at this, could you give me a motherboard that is comparable in any other way? I'd also like it to be cheaper if possible.

---

### Post by cascade9 on 2011-02-12
If you are really worried abotu prices, this is what I would get- 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813138179](http://www.newegg.com/Product/Product.aspx?Item=N82E16813138179)

The only possible problem is that board has no USB 3.0. Not that big a deal really, eSATA is better than USB 3.0 anyway. 

I'd consider getting a slightly better board, the newer 870/SB850 chipsets do SATAIII (770/SB7XX only has SATAII). The newer 870 boards might support future AMD CPUs that the 7XX boards dont as well. The are a bit more than 79.99 though, you are probably looking at $85-100.

---

### Post by TheBritishEditor on 2011-02-12
Is there a 880/SB710 that doesn't have integrated graphics?

---

### Post by cascade9 on 2011-02-12
Nope. All 880 chipsets have onboard video.

---

### Post by TheBritishEditor on 2011-02-12
Then I might as well get the motherboard I already had picked. I don't know if I want to get an old model. XD

---

### Post by cascade9 on 2011-02-12
> **TheBritishEditor said:**
> Then I might as well get the motherboard I already had picked. I don't know if I want to get an old model. XD

The only thing that is newer in the 880/SB710 setup (like the asrock 880GXH) compared to a 770/SB710 (like the biostar A770E3) is the northbridge/onboard video. BTW, onboard video is why the asrock is $20 more expensive, and since you are getting a video card its a wasted $20.... 

If you really dont 'want to get stuck with an old model' spend the extra $5-20 and get a 870/SB850 setup.

---

### Post by TheBritishEditor on 2011-02-17
Here we go again. Please don't critique what I have here unless it is changing something so that it works with Ubuntu. I need to know that all these parts are compatible with each other and Ubuntu. Thanks. As always I have a HDD, Optical, and PSU sitting around already.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103808](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103808)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813157198](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157198)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814125325](http://www.newegg.com/Product/Product.aspx?Item=N82E16814125325)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16820104206](http://www.newegg.com/Product/Product.aspx?Item=N82E16820104206)

---

### Post by TheBritishEditor on 2011-02-20
Bump.. Are THESE parts compatible 100% with Ubuntu. If not immediately, where can I get the drivers, and how would I install them. Thank you. I already have a PSU, Optical, and HDD as stated.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103808](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103808)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16811119233](http://www.newegg.com/Product/Product.aspx?Item=N82E16811119233)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128443](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128443)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814125325](http://www.newegg.com/Product/Product.aspx?Item=N82E16814125325)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16820104206](http://www.newegg.com/Product/Product.aspx?Item=N82E16820104206)

Please don't critique what I have here, I just need to know if this works with Ubuntu.

---

### Post by cascade9 on 2011-02-20
No problems with the CPU, GPU, or RAM. Cases, the OS doesnt know, let alone care. 

GA-870-UD3 should be fine. I havent checked the asrock. 

You could hit problems with the PSU if you have an older model, due to the voltage rails. Older PSUs had big 5v rails, newer PSUs have bigger 12v rails. If the 12v rail doesnt deliver enough power you will get segfaults, crashing and/or other oddness that might make you think that the new hardware is bad. I've had it happen.

---

### Post by TheBritishEditor on 2011-02-20
It's not that old, but it's old enough to be deactivated on Newegg. It has the 12v rails.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16817103936](http://www.newegg.com/Product/Product.aspx?Item=N82E16817103936)

Please disregard the bad reviews, I've tested it over and over again, the PSU works absolutely fine.

I'm glad to know that the parts are compatible, I'll be ordering them soon.

---

### Post by cascade9 on 2011-02-21
All ATX power supplies (and even AT) have 12v rails. The problem is if the 12v rail is low powered. 

That should have enough 12v power.

---

