---
title: "Asus on board Graphic Card Driver"
date: 2010-03-31
forum: Hardware
---

### Post by cyberyder on 2010-03-31
Hi All,
I'm new but not that new to linux. However, when it gets to build/run edit File for graphic card i usually suck.  

I went to the ASUS website and they gave me a .run for the graphic driver. 

I have no clue how to make this work. I'm trying to use tutorials i find but none of them works A1.

anyway, my graphic card is ASUS p5VD2-MX SE.  Anyone can help me out?thanks a lot

---

### Post by IcarusR on 2010-04-01
> my graphic card is ASUS p5VD2-MX SE

That is your motherboard not graphics card.

Post output of this terminal command so we can identify your graphics card.

```
lspci
```

---

### Post by Mark Phelps on 2010-04-01
According to Google, the onboard graphics is VIA UniChrome P4M890 -- not good!

---

### Post by cascade9 on 2010-04-01
> **Mark Phelps said:**
> According to Google, the onboard graphics is VIA UniChrome P4M890 -- not good!

It is (both VIA Unichrome and not good)- 

[http://www.asus.com/product.aspx?P_ID=SQkGx1Z6auj7xRGe&templete=2](http://www.asus.com/product.aspx?P_ID=SQkGx1Z6auj7xRGe&templete=2)

As for what to do- either try the openchrome driver- 

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

Or manually install the Via .run driver. Which seems to be a right pain from what I'm seeing... It might be a lot easier to just buy a really cheap PCIe video card. If you got an nvidia card, it doesnt really matter what you get, its going to be better than VIA UniChrome.

---

