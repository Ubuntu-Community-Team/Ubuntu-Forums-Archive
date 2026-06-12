---
title: "Need New Video Card"
date: 2007-12-26
forum: Hardware &amp; Laptops
---

### Post by BITstate on 2007-12-26
I have a ATI rage 128 card, apparently there is no support for this card, so I have to change it so that I can get all graphics in 7.10 working:(

Can someone suggest a good replacement?

I don't play games, I just need good card that will allow me to take full avantage of the graphics in ubuntu without costing a bomb, a Nvidia card has been suggested so far.

I am a bit putout that I have to replace a part of machine just because of a driver issue,
I dont wish to spend money if there is a downloadable solution.

Thanks for any ideas

---

### Post by jespdj on 2007-12-26
ATI's drivers for Linux are unfortunately still not really great, although AMD/ATI has promised (months ago) to improve them.

nVidia's drivers are much better. If it's for a desktop PC, I'd suggest getting a 8600 series card. It's one step below the most powerful cards (the 8800 series), but a lot cheaper and still quite powerful. If you want it even cheaper, look at for example a 8500 series card, or a card of the older 7xxx series.

My desktop has a 8600 GTS, my laptop a 8400M GS, and they both work without any problem. Activating the nVidia driver after installing Ubuntu was just a mouse click, and Compiz Fusion desktop effects all work great.

---

### Post by Yellow Pasque on 2007-12-26
What kind of video card slot do you have?
If it's AGP, is it possible for you to determine what kind of AGP?
([http://en.wikipedia.org/wiki/Accelerated_Graphics_Port](http://en.wikipedia.org/wiki/Accelerated_Graphics_Port))
Was it a manufactured computer or one you built yourself?

If you don't have an AGP expansion slot then you can use a PCI video card, like a GeForce 6200 or Radeon9250.

Try to get something without a fan.

---

### Post by Tadock on 2007-12-26
> **jespdj said:**
> ATI's drivers for Linux are unfortunately still not really great, although AMD/ATI has promised (months ago) to improve them.

nVidia's drivers are much better. If it's for a desktop PC, I'd suggest getting a 8600 series card. It's one step below the most powerful cards (the 8800 series), but a lot cheaper and still quite powerful. If you want it even cheaper, look at for example a 8500 series card, or a card of the older 7xxx series.

My desktop has a 8600 GTS, my laptop a 8400M GS, and they both work without any problem. Activating the nVidia driver after installing Ubuntu was just a mouse click, and Compiz Fusion desktop effects all work great.

I must agree I have a 8600 in my desktop at home and runs Ubuntu w/o any problems whats so ever. But, to make a final recommend I need to knew whether its a AGP or PCI-E slot for your card.

---

### Post by Yellow Pasque on 2007-12-26
> **Tadock said:**
> I must agree I have a 8600 in my desktop at home and runs Ubuntu w/o any problems whats so ever. But, to make a final recommend I need to knew whether its a AGP or PCI-E slot for your card.
Rage 128 is a very old card. The system is certainly not PCI-E. The OP might have to be cautious of which type of AGP he/she has 

[I]> AGP cards are backward and forward compatible within limits. 1.5 V-only keyed cards will not go into 3.3 V slots and vice versa, though "Universal" slots exist which accept either type of card. AGP Pro cards will not fit into standard slots, but standard AGP cards will work in a Pro slot. Some newer cards, like NVIDIA's GeForce 6 series or ATI's Radeon X800 series, only have keys for 1.5 V to prevent them from installing in older mainboards without 1.5 V support. Some of the last modern cards with 3.3 V support were the NVIDIA GeForce FX series and the ATI Radeon 9500/9700/9800(R350) (but not 9600/9800(R360)).

It is important to check voltage compatibility as some cards incorrectly have dual notches and some motherboards incorrectly have fully open slots. Furthermore, some poorly designed older 3.3 V cards incorrectly have the 1.5 V key. Inserting a card into a slot that does not support the correct signaling voltage may cause damage.[/I] -- [http://en.wikipedia.org/wiki/Accelerated_Graphics_Port](http://en.wikipedia.org/wiki/Accelerated_Graphics_Port)

---

### Post by Tadock on 2007-12-26
> **Temüjin said:**
> Rage 128 is a very old card. The system is certainly not PCI-E. The OP might have to be cautious of which type of AGP he/she has 

 -- [http://en.wikipedia.org/wiki/Accelerated_Graphics_Port](http://en.wikipedia.org/wiki/Accelerated_Graphics_Port)
Your right. I suggest this[ Nvidia Geforce 7600]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814145135"). But, I would ask for a second opinion about it.

---

### Post by daschmidty on 2007-12-26
Well the ati drivers have improved quite a bit to be honest. And if you buy a lower end ati card that can use the opensource 'radeon' driver without needing fglrx, it is not a bad way to go. I just bought a geforce 6200 (256mb) for my linux box and my performance is maybe about 15% better then with my old ati x300 (128mb) that i bought four or so years ago using the opensource driver. The only problems with ati come with the high end cards, so I would say looking for an entry level card pick whatever is cheap.

---

