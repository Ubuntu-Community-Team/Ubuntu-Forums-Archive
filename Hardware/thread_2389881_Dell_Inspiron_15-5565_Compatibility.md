---
title: "Dell Inspiron 15-5565 Compatibility"
date: 2018-04-22
forum: Hardware
---

### Post by Deleted20200712 on 2018-04-22
Ok, so I finally got a good job and will have enough money to buy a new laptop on May 1st.  After scouring newegg, I found this Dell Inspiron 15-5565:  [https://www.newegg.com/Product/Product.aspx?Item=9SIA8X55HR7496](https://www.newegg.com/Product/Product.aspx?Item=9SIA8X55HR7496)

As I've been doing since forever, I'll be wiping the hard drive, putting vanilla Windows on there (without all the extra bloatware), then putting Ubuntu on as my main OS (just in time for 18.04!).  I just want to check that **a) I won't brick the laptop, b) the hardware is all compatible and c) I can play at least my main games on it**.

When I look at the list of Ubuntu certified hardware for Dell ([https://certification.ubuntu.com/desktop/models/?category=Laptop&vendors=Dell](https://certification.ubuntu.com/desktop/models/?category=Laptop&vendors=Dell)), the closest to this model I find is a Dell Inspiron 15-5568 ([https://certification.ubuntu.com/hardware/201603-20843/](https://certification.ubuntu.com/hardware/201603-20843/)), which uses Intel hardware for both the processor and video cards, while the one I plan to buy uses AMD for both.

IN ADDITION, the card listed for mine is "AMD Radeon R8 M445DX" which doesn't actually exist; it's "AMD Radeon R8 M445DX is a Dual Graphics Crossfire combination of  integrated R7 Series (in FX-9800P) and a dedicated R7 graphics on board."  According to this page ([https://www.notebookcheck.net/AMD-Radeon-R8-M445DX-Dual-Graphics-Benchmarks-and-Specs.169457.0.html](https://www.notebookcheck.net/AMD-Radeon-R8-M445DX-Dual-Graphics-Benchmarks-and-Specs.169457.0.html)), "The AMD Radeon R8 M445DX is a Dual Graphics combination of the  integrated Radeon R5 (Bristol Ridge, e.g. in the A10-9600P) and a  dedicated [Radeon R7 M440]("https://www.notebookcheck.net/AMD-Radeon-R7-M440-Benchmarks-and-Specs.169455.0.html")  graphics card. It was introduced in mid 2016 for entry level multimedia  laptops. The R8 M445DX runs both cards in hybrid crossfire mode and  renders games in AFR mode (alternate frame rendering) that renders a  frame alternately on each card. Therefore, the Dual Graphics needs  driver profiles for each DX 11 game to work properly and often suffers  from [micro stuttering]("https://www.notebookcheck.net/Micro-Stuttering-with-SLI-or-CrossFire.57232.0.html")."

Now, when I go to AMD's website to look up if they have a driver for it, I can choose "Radeon R7 M4XX Series" but only Windows drivers are available.  Thus I assume no Linux driver is available...?

If that's the case, I would be using the open source driver, correct?  Now of course I'm not against this at all; after all I got into Linux originally because I love the ideology/philosophy behind FOSS.  Plus from what I've read the open source driver for AMD is actually pretty good.  The only thing I want to make sure is that this card using the open source driver will be able to run games better than the card I am currently using, an NVIDIA GeForce 410M in a Sony Vaio Laptop VPCEG (laptop bought in January 2014; pretty sure it was over a year old when I bought it new for $600), using the proprietary NVIDIA driver.  And tbh, 90% of my gaming is Dota2, which runs smoothly enough to play with my current card, and only causes the computer to freeze about 1 out of every 15 games.  Other less resource-intensive games run pretty well.

Thoughts anyone?

---

### Post by cruzer001 on 2018-04-22
About two months ago I bought a refurbished (class A) Dell Precision off of eBay.

Intel i7 quad core, 12G ram, ssd & hhd, 17" screen for $400 US.

Came with win10, but I have 18.04 installed.

Pay attention to the rating.
Class A = Like new
Class B = Looks used
Class C = Been abused

And only buy from top rated sellers.

---

### Post by kerry_s on 2018-04-22
i think you should get something that can atleast run virtualbox just in case, so you have the option to run linux in vm with out issues.
this:
[https://www.newegg.com/Product/Product.aspx?Item=9SIA8X55HR7496](https://www.newegg.com/Product/Product.aspx?Item=9SIA8X55HR7496)

has amd-v disabled so no vm support

---

