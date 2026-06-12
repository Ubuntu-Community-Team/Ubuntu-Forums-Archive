---
title: "Sierra MC8755 Dell M1330"
date: 2009-01-02
forum: Hardware
---

### Post by Keithodulaigh on 2009-01-02
Hi All,
I bought a Sierra Mc8755 for my new Dell M1330. Cellular devices is enabled in BIOS. However, cellular devices is listed as {none} also in the BIOS after I inserted the card. 

I've tried doing lspci in Ubuntu and it doesn't show up either. 

Is there anyone here who has used the MC8775 in the Dell M1330 with success? If so, what BIOS version were you using? I'm on A14.

I bought the card on Ebay so chances are that it's faulty! I've also tried the card in W!ndow$ and it doesn't show up in device manager either...

My other suspicion is that the BIOS might only allow the Dell 5520 card to be used but since I've read about someone using the Latitude's 5530 card I don't know.

Anyone able to help??

Thanks to anyone who tries!

---

### Post by Keithodulaigh on 2009-01-04
Anyone?

---

### Post by CJay554 on 2009-01-04
Try this:
[http://foomagic.org/wiki/index.php/Using_the_Sierra_mc8755_WWAN_card_under_linux](http://foomagic.org/wiki/index.php/Using_the_Sierra_mc8755_WWAN_card_under_linux)

---

### Post by jeevas.v on 2010-02-25
> **CJay554 said:**
> Try this:
[http://foomagic.org/wiki/index.php/Using_the_Sierra_mc8755_WWAN_card_under_linux](http://foomagic.org/wiki/index.php/Using_the_Sierra_mc8755_WWAN_card_under_linux)

Hi,

If you want to use Sierra or any other thirdparty WWAN card in XPS m1330 laptops then you have to downgrade your BIOS to either A00/A01/A02(I am using A02 which is still currently available at the dell support site). All bios versions above A02 have  HW white list which blocks non dell parts. 

Once you downgrade the BIOS to A02 everything works like charm. I have perfect connectivity using Ubuntu 9.10(karmic)

---

### Post by CJay554 on 2010-03-02
Wow, Dell is trying to be apple? :/

---

