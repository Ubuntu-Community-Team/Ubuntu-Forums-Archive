---
title: "Building low power box?"
date: 2008-11-17
forum: General Help
---

### Post by paulsjv on 2008-11-17
Hi,

I was doing some searches to try and find a small machine that uses low power (2 to 3 watts).  I know there is a company called CherryPal that does this but it's $249 for the box which has the following:

> 
Freescale’s MPC5121e mobileGT processor, 800
MIPS (400 MHz) of processing
256 MB of DDR2 DRAM
8GB NAND Flash-based solid state drive
(increased from 4GB C100)
WiFi 802.11b/g Wi-Fi
Two USB 2.0 ports
One 10/100 Ethernet with RJ-45 jack
One VGA DB-15 display out jack
Headphone level stereo audio out 3.5mm jack
9vDC 2.5mm 10 watt AC-DC adapter power supply
Weighs 10 ounces
1.3” high, 5.8” x 4.2” wide

Not all that great for the price, IMO.  So I was thinking I could probably build one myself cheaper with more internal power and with Ubuntu!

Thing is that I haven't built a computer since about 2000 and it was your usual desktop.  Now I'm wanting to build this low power quite Ubuntu box.

I'd really like to have the following:
[LIST]
[*]1 gig CPU
[*]1 gig RAM
[*]16 to 32 gig SSD
[/LIST]

Any thoughts on where I should start with regards to hardware for this box?

Thanks!

---

### Post by paulsjv on 2008-11-18
*bump*

---

### Post by sdennie on 2008-11-18
Something like this is probably what you are looking for: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813130105](http://www.newegg.com/Product/Product.aspx?Item=N82E16813130105) (or any other motherboard/cpu combo with a VIA C7 chip).  I doubt if it will get anywhere near 2-3W of power (you'd have to research it a bit) but, it is x86 compatible and otherwise meets your specs (once you buy the RAM/SSD).

---

### Post by easoukenka on 2008-11-19
Maybe just buy a EEE laptop they are great on power and you can just plug in your own keyboard mouse monitor etc.  Buy an SDCARD for more space and you got all you asked for

---

### Post by dcstar on 2008-11-19
6W:

[http://www.fit-pc.com/new/](http://www.fit-pc.com/new/)

---

### Post by SeanBlader on 2008-11-19
Memory and processor take up wattage. In the end the question is, what are you going to do with it? Then you should try and build your low power specs from there. Just building a low power box isn't a destination on it's own unless you plan to resell it. But for two or three watts you probably can't run an Intel chip even an atom, which is why CherryPal uses Mips.

---

### Post by timberline5 on 2008-11-19
You should look into some variant of itx boards. They are small and efficient, even fan-less and they are x86 so ubuntu will work.

[http://www.mini-box.com/site/resources/html/powersimulator.html](http://www.mini-box.com/site/resources/html/powersimulator.html)

that will give you an estimate of what kind of power you would use with different boards.

---

### Post by th00ht on 2009-02-06
> **paulsjv said:**
> 

Any thoughts on where I should start with regards to hardware for this box?

Thanks!

[http://www.via.com.tw/en/products/embedded/artigo/](http://www.via.com.tw/en/products/embedded/artigo/)

---

