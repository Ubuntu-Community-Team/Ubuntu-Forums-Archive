---
title: "Ubuntu on HP ENVY 15-3040NR"
date: 2012-03-26
forum: Hardware
---

### Post by farqad on 2012-03-26
Hi you all,
    I'm looking for a new laptop and my choice has focused on this:

**HP ENVY 15-3040NR**
Processor: Intel Core i7-2670QM
Graphics card: AMD Radeon HD 7690M XT switchable graphics with 1024MB GDDR5 memory

Since I would like to use Linux on it, does someone know if Ubuntu **works well** with this laptop or if it has some a problem?

Thanks a lot!!

---

### Post by anton79ru on 2012-04-03
Hi mate, not sure if you still need a reply on this one, but still (what I'm saying is valid for 12.04):

1. You will need to set the switchable graphics to 'fixed' in BIOS.

2. Radeon HD 7690M is not 'officially' supported by the fglrx proprietary driver, nor by the open-source driver. It will be recognized as 6770M. I'm having problems with the video card.

2.1. Fglrx won't install correctly from the Ubuntu repository. You will need to install it manually as described [here]("http://help.ubuntu.com/community/BinaryDriverHowto/ATI").

2.2. Even though fglrxinfo reports the driver to be installed correctly, when switching users or simply logging off, the system often crashes to low graphics mode or just a screenful of text strings which I cannot understang because I'm a newbie. At least I saw "fglrx" and "RIP" in the same string, which just can't be good :)

---

### Post by hybenz on 2012-04-03
The 2nd gen HP Envy 15 with ATI 5830 is indeed a powerful laptop.  it's a good buy Considering its performance and look (slim and portable).  but.....thumbs down for its battery life.. [FONT=Garamond][SIZE=1][[COLOR=White]ink[/COLOR]]("http://www.inkjetsuperstore.com/")[/SIZE][/FONT][FONT=Garamond][COLOR=White][SIZE=1]
[/SIZE][/COLOR][/FONT]

---

### Post by Goronok on 2012-04-03
Envy laptops, in my opinion, are NOT good with the latest versions of Ubuntu or Mint.  I have experience with the 13 & 17" derivatives and both perform well, but Ubuntu has problems interfacing with the bios and cooling/thermal aspects of the notebook. The laptops would sit around 60-70C - even idling.  I've spent a great deal of time researching a fix for this, but it doesn't appear that a work around currently exists. You can't even install lm-sensors or fancontrol on these notebooks as the bios does not allow you to control fan speed.  Basically the notebook becomes a flattop for you to cook eggs/bacon on :P  

I'd love for someone to prove me wrong - I'd certainly love to run Ubuntu on my Envy 13.  If not, i'd suggest looking elsewhere if your intent on running Ubuntu :-(

---

