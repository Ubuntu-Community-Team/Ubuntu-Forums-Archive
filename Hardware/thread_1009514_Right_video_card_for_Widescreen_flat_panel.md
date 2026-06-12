---
title: "Right video card for Widescreen flat panel"
date: 2008-12-12
forum: Hardware
---

### Post by Aijse on 2008-12-12
Hi all,
I have a question that is not really Ubuntu related but im sure there are alot of you out here who can help me with it.

My girlfriend needs a new monitor for her pc, she found a few nice ones with DVI connection and resolutions of 1680x1050 I believe.
Her onboard videochip has no DVI connection so we decided to look for a videocard  (new or maybe ebay, atleast budget). The thing is though that most of the time only the analoge max resolution from the card is given. So I'm wondering how I can find out which card actually supports the 1680x1050 resolution through DVI. It must also be an AGP card since there is no PCI-E slot.
If you have any suggestions on good cards or you can point me in the good direction what I have to pay attention for please leave a message. All help appreciated
Greetings

---

### Post by Aijse on 2008-12-13
any one can help me out which video cards are good enough for the 1680x1050 widescreen reolution?

---

### Post by madman92 on 2008-12-13
1680x1050 shouldn't be a limiting factor; most integrated graphics solutions should be able to handle that. Most monitors will have both ports in the back: both VGA and DVI. If not, you don't need to buy a new graphics card, unless using a DVI port is absolutely necessary (for whatever reason). Just buy a dongle: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814999901](http://www.newegg.com/Product/Product.aspx?Item=N82E16814999901). 


If you are still going to go out and get a new video card, what is the computer going to be used for?

Anyway post back with what kinda computer/integrated graphics the computer has.

---

### Post by MonkeyPaw on 2008-12-13
Yeah, really, resolutions are only limited by the amount of RAM on the card, and I think something as low as 32mb would cover that resolution. However, such old cards may not do much for accelerating graphical interfaces, but even an old ATI 8500 will handle Ubuntu's niceties. I'd just go for an ATI or nVidia card. Even the most basic of models should be good enough if you're not playing games. No sense getting a power-hungry card if you're never going to need it.

---

### Post by Aijse on 2008-12-14
Hi thanks for your replies!
This is the onboard video chip that is in now VIA/S3G UniChrome IGP. I believe this one is realy not capable of the 1680x1050 resolution. But if you feel it is then I am glad to hear this from you.
Also if this chip is not capable of producing the right resolutions, could you give some advice on old model video cards. For example would a radeon 9550 be good enough or a geforce 6200?
Thanks in advance

---

### Post by nick09 on 2008-12-14
A ASUS AH3450 should get you what you want for a resolution:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814121273](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121273)

Specs off of CNET:
[http://reviews.cnet.com/graphics-cards/asus-ah3450-htp-graphics/4507-8902_7-33289502.html?tag=mncol;rnav](http://reviews.cnet.com/graphics-cards/asus-ah3450-htp-graphics/4507-8902_7-33289502.html?tag=mncol;rnav)

Ubuntu 8.10 even comes with the drivers you need; though I'd recommend you grab the proprietary drivers from Hardware Drivers in the Administration section because I have experienced slight visual(blurry) problems from the open source drivers. Plus you can also overclock the card via the command line by entering aticonfig(CLI based) in the terminal.

---

