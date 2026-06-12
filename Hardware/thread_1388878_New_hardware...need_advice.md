---
title: "New hardware...need advice"
date: 2010-01-23
forum: Hardware
---

### Post by MonsterDuc on 2010-01-23
Here is my dilemma:  
I am building a new PC.  It will not be used for any games, but will contain lots of files and serve as the households "media center".  I have an older PC that I'd like to use the parts I can from.
 
What I currently have:
- An old 250W power supply
- A couple old IDE drives 160GB
- An Nvidia GF4 Ti4200 128MB graphics card
 
So, with the objective of keeping it cheap, and having a well functioning ubuntu system, I have created two options so far; one AMD and one Intel.  Would be great with some feedback/thoughts!
 
Option 1:
CPU:          Athlon II X2 245 2 MB (AMD PiB)
Motherboard:  ASRock M3A785GM-LE/128M (built in Graphics card)
RAM:          Kingston ValueRAM 1 x 4 GB
 
Option 2:
CPU:          Pentium E6300 2 MB (Intel Boxed)
Motherboard:  ASRock G31DE (built in Graphics card)
RAM:          Kingston ValueRAM 1 x 4 GB

Any thoughts on AMD vs Intel?
 
For both options I was planning on using one of my old IDE drives, and the old power supply, but I am not sure if the old power supply will be sufficient? 
 
I also looked for motherboards with built in graphics card so I didn't have to use the old one I have, although I don't know if the old one OR the built in is any good or bad.  Interested if anyone thinks it would be beneficial to use the old graphics card, and pick a cheaper motherboard without built in graphics card?  Then I could use the saved money on a cheap SATA disk.  Remember, part of my fun here is to keep it cheap so I can brag about my "high performing" system that I hardly paid for :)
 
Thoughts / Advice / Warnings all welcome!  

Thanks!

---

### Post by cascade9 on 2010-01-23
250 watts might just be enough..but 'old' is worrying. I would get a new power supply.

Your 160GB IDE drives should be usable. Be aware, most motherboards now only have 1 IDE channel, so thats maximum 2 drives. So if you want to use 2xIDE HDDs, you will need to buy a SATA DVD drive (they pretty cheap though). Or a PCI/PCI-E IDE expansion card (I wouldnt do this, and it would cost almost as much as a SATA DVD drive). 

On AMD vs Intel, AMD always has a better price/performance. I'd go for AMD if your on a budget, every time.

Intel onboard video tends to be lame compared to nVidia or ATI. ATI does have, well, issues under linux at tiomes, so maybe you would be better of getting a motherbaord with onboard nVidia video. Something liek this- 

[http://www.gigabyte.com.tw/Support/Motherboard/CPUSupport_Model.aspx?ProductID=3281#anchor_os](http://www.gigabyte.com.tw/Support/Motherboard/CPUSupport_Model.aspx?ProductID=3281#anchor_os)

You wont find any modern motherboards that support AGP still, so your old GF4 4200 is now retired. Dont worry that much, the onboard ATI and nVidia video should be at least as faster, if not a lot faster than the old GF4 series.

---

### Post by MonsterDuc on 2010-01-24
Thanks for that.  Appreciate the thoughts!

The motherboard you suggested looks good, although I'd like to keep the size ATX if possible.  Wasn't aware of the ATI vs Nvidia part so we'll look for something with built in Nvidia in ATX form factor, and I'll be going down the AMD route based on your suggestion.

Thanks!

---

### Post by cascade9 on 2010-01-24
This ought to do it-
[SIZE=2]
ASRock K10N78 AM2+/AM2 NVIDIA GeForce 8200[/SIZE]

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813157159](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157159)

If you cant find an ATX nVidia 8100/8200/8300 chipset (or newer) motherboard, dont worry to much. You can get 8400GS/9400GT nVidia cards for about $30 US these days, and a ATI 770 chipset (no oboard graphics) is about the same cost or a little more than the nVidia chipset motherboards. 

BTW, you will see older GeForce 7025 chipset motherboards around. They probably arent any better than the ATI chipsets with onboard video, and are getting quite old now. The 750a/780a might be worth a look, but be careful..some of them will not support the CPU you want to use ;) Most of them are about as much as a ATI 770 chipset motherboard + a video card as well. 980a nVidia chipsets do what you want, but are priced a bit to high. More than a 770 + video card anyway ;) 

Edit- I should really check before I post stuff. That asrock board I posted above doesnt support Athlon II chips :|

---

### Post by MonsterDuc on 2010-01-24
Thanks for your help first of all! 

I am currently considering the ASRock M3A785GM-LE/128M ([http://tinyurl.com/yfdd9vc](http://tinyurl.com/yfdd9vc)) and the one you suggested from Gigabyte (although rev 1.2 instead of 1.3: [http://tinyurl.com/yhr4bke](http://tinyurl.com/yhr4bke)).

The Gigabyte one uses DDR2 SDRAM instead of DDR3 (DDR2 being a bit cheaper and could easily pickup something used), AND it has the Nvidia chipset you recommended.  The ASRock is ATX, but AMD 785G Chipset.  Price is about the same.

Guess I can sacrifice the full ATX... 

Thanks again!  Much appreciated!

---

### Post by cascade9 on 2010-01-25
No problem. I love looking at hardware porn...its nearly as good as going out to buy the stuff :D 

Both micro-ATX boards though. 

There are full ATX 8200/8300 chipset motehrboards- 

Asus M4N87 Pro-

[http://www.asus.com/product.aspx?P_ID=lco8LZWTqWIhdLmv&templete=2](http://www.asus.com/product.aspx?P_ID=lco8LZWTqWIhdLmv&templete=2) 

Though from the pricing of that board, it wopuld be cheaper to get a 770 + nVidia card. :| 

Just a pity that so many hardware manufacturers have disappeared over the last few years....abit, epox and a few of my other prefered brands, gone :( 
[B]

[/B]

---

