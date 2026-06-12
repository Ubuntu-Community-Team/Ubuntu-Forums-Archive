---
title: "Suggestion for PCI Express x16 graphics card"
date: 2011-02-06
forum: Hardware
---

### Post by IanWood on 2011-02-06
Hi all,

I would like some advice about a suitable PCI Express x16 graphics card. 

I have a HP small form factor PC which has a PCI Express x16 Matrox P960 card in it which won't work with any Ubuntu since 8.10 (due to the X server changing a lot and breaking support, from what I have read).

The problem is its being a long time since I have bought a graphics card so don't know what to get. 

I want it to:
Have two DVI outputs (for two widescreen TFT screens)
Be able to do Compiz
Be able to fit in PCI Express x16 slot.
Work with Ubuntu 10.10 and future releases. 

I am not too bothered about games. If it could have output for HDMI or similar for TV that would be nice. 

I am confused as to weather to get an ATI or NVidia or something else.

Please can someone point me in the right direction.

Thanks for you help,

Ian

---

### Post by cascade9 on 2011-02-06
I'd give 10.04/10.10 a try before you go buying a new card. You nevwer know, maybe those reports you saw are outdated. 

ATI or nVidia are pretty much your only choices now. The days of lots of video card manufacturers are gone. :( 

SFF computer normally use 'half height' cards, so be check that before you buy anything. 

I'd probably go for a nice cheap nvidia GT210, GT220 or GT430.

---

### Post by IanWood on 2011-02-06
Thanks cascade9

I have already installed 10.10 and I couldn't compile the Matrox driver, then I read the release notes saying it works with 8.10 and then did some more Googling. I have had problems before with Matrox cards and in the past needed to revert from an upgrade from 8.04 to 8.10 for instance.

I machine is pretty small so am a little worried about buying a card that's too big, but most shop sites have the dimension of the card so I should be ok.

Is the support for Nvidia better than ATI now or the other way around? I don't really mind which I get I just want it to work! 

Thanks again,

---

### Post by cascade9 on 2011-02-06
As long as the display works, compling the matrox driver isnt something you need to do. ;) 

Do yuo know what model computer it is? I can check how big a card you can get in if you can tell me the mdoel. 

For desktops, nvidia is still probably better than ATI/AMD. For now anyway.

---

### Post by IanWood on 2011-02-06
Thanks again for your help.

Its a HP DC7700 Small Form Factor.

I needed to compile the driver to get the dual head working. 

At the moment the vesa driver only drives one monitor and just a small square of the whole wide screen, and its fuzzy!

I imagine its not hard to buy a correct card but I have no idea what's good and what's bad,

---

### Post by cascade9 on 2011-02-06
Doh....dual head. That might be a problem then. I though it was possible to get dualhead going with the open source matrox drivers, but I cant test that- the only matrox cad I have is single head only (and its so old that its not funny anyway). 

As long as its a HP DC7700 Small Form Factor you can get a decent card in there no problem- 

[http://h18000.www1.hp.com/products/quickspecs/12253_div/12253_div.HTML#Technical%20Specifications](http://h18000.www1.hp.com/products/quickspecs/12253_div/12253_div.HTML#Technical%20Specifications)

That doesnt show me how much clearance here is between the PCIe slot and whatever could be in the way, but I did find this- 

[http://www.trustedreviews.com/pcs/review/2007/07/27/HP-dc7700-SFF-GE008ET-/p2](http://www.trustedreviews.com/pcs/review/2007/07/27/HP-dc7700-SFF-GE008ET-/p2)

Seems like you should have no problems with most of the GT210/220/430 cards, as long as you get a half height version. That said, the only card I can think of that I can tell you should have 0 issues fitting is an asus ENGT430. 

I'm pretty sure that other GT card would fit, but some of them are longer than others. The ENGT430 is only a tiny bit longer than the end of the PCIe slot, so I'm confident it will fit just fine. ;)

---

### Post by IanWood on 2011-02-06
With a newer Matrox card on my work machine I have three screens working well, but this older machine and card I can't :(

How much ram do you think would I need to get to get Compiz working, considering the machine I am putting it in I don't want to get a too capable card and waste money. 

Would you cards you mention do dual head?

Ta

---

### Post by cascade9 on 2011-02-06
I actually dont know very much at all about compiz (I dont use it at all). I cant imagine that you would have any problems with 1GB (the current recommended minimum RAM for ubuntu), and it should run on far less than that. 

Those GT card should do dual head just fine. The ENGT430 has 1 x VGA, 1 x DVI and 1 x HMDI. So if you wanted 1 x VGA + 1 x DVI, etc, its just plug and go. For 2 x VGA, you'd need a DVI-> VGA adpater (you sometimes get these bundled with video cards, if not they are cheap). For 2 x DVI, HDMI -> DVI adapter (cheap again). 

That is farily typical of the GT cards. Some of have only DVI + HDMI

The DVI port on at least some of the GT cards is 'dual link DVI' (meaning you can use a DVI-> 2 x DVI adapter instead of a HDMI-> DVI adapter) but IIRC they are more expensive than a HDMI-> DVI adapter. The only reason to use one IMO would be so you can disable monitor #2 and use the HDMI to connect to a TV.

---

### Post by IanWood on 2011-02-06
I don't use Compiz either, but would like to be able to try it. 

Sorry, I meant graphics RAM, the machine itself has 2GB. 

I didn't release you could get a HDMI-> DVI adapter. That's good to know. 

So, to get dual head with 2 DVIs, which I understand to be better quality than VGA, I either need 2 DVIs, or a DVI and a HDMI?

Is the quality the same between DVI and HDMI->DVI?

I don't think that I would need to connect to both the monitors and a TV so I think two DVIs or one DVI and HDMI would be fine.

Where would you suggest I get this from? Amazon's site seems a little difficult to navigate and I haven't used Ebuyer or Scan for ages. 

Good advice, thanks again.

---

### Post by cascade9 on 2011-02-06
No problem, gald to help ;) 

Video RAM for needed for compiz? Far,far less than you will find on any GT card. IIRC it use to run fine on 128MB cards (though it can be screwy if you have less than 128MB. 

> NVIDIA  

After a while, windows begin to go black 

This is the infamous Black-Window Bug with the NVIDIA driver. It is caused by the graphics card running out of texture memory, and therefore all remaining windows (which are textures) will be black. If you have less than 128MB of video memory, disabling blur, and launching Compiz with --indirect-rendering will reduce the appearance of the bug. 

[http://wiki.compiz.org/FAQ](http://wiki.compiz.org/FAQ)

All the GT cards I've seen are 512MB+. ;) 

HDMI and DVI are pretty much the same. The only big difference is DVI is video only, HDMI will also do audio (which is why its better to hook up to a TV with HDMI in most cases). 

DVI (digital) should be better quality than VGA (analog). Some people, with some monitors can notice the difference, other situations you might not see a difference. It all depends on yoru card, monitor and eyes. 

Where are you? That would make a difference as to where to source the card from.

---

### Post by IanWood on 2011-02-06
I am in London, UK. Didn't notice you were in the Oz. 

I expect I will be fine with a GT210.

This one looks promising. [http://www.ebuyer.com/product/176604](http://www.ebuyer.com/product/176604) 

Yours [http://www.amazon.co.uk/ASUS-GeForce-PCI-Profile-Bracket/dp/B0046Y4ONK/ref=sr_1_1?ie=UTF8&qid=1297001038&sr=1-1](http://www.amazon.co.uk/ASUS-GeForce-PCI-Profile-Bracket/dp/B0046Y4ONK/ref=sr_1_1?ie=UTF8&qid=1297001038&sr=1-1) is around twice the price and may be overkill for the machine I am putting it in. 

Thanks again

---

### Post by cascade9 on 2011-02-06
Didnt notice I was from oz? Thats beause I lived in a British Dependent Territory and leant how to be civilised. :lolflag: 

You should will be fine with a GT210. 

If you want to be _really_ sure though, I'd take the top off your computer and measure how much length there is between the backplate (where the card 'screws in') and the CPU. The EN210 is 7'' long as far as I can tell, and I'd guess that you've got more like 7.5-8'' of space

Heres a great site, I use the .au version quite a bit- 

[http://www.staticice.co.uk/cgi-bin/search.cgi?q=EN210&spos=1](http://www.staticice.co.uk/cgi-bin/search.cgi?q=EN210&spos=1)

Seems like you can get the EN210 cheaper that from ebuyer. Not that means you should go to a cheaper place, sometimes its not worth it. But you never know, maybe some place in london that is handy will have the card you want. I'd much rahter buy over a counter than online if I can get similar prices.

---

### Post by IanWood on 2011-02-06
That's great - definitely think I know what to get now. 

Thanks for your help. 

Cheers

---

### Post by cascade9 on 2011-02-08
No problem, good luck (not that you should need any luck ;) )

---

### Post by IanWood on 2011-02-11
> **cascade9 said:**
> No problem, good luck (not that you should need any luck ;) )

As always you are right. Bought the ASUS ENGT430 as you suggested would work and fit. Perhaps a bit overkill but more future proof.

Just fitted it and asked Ubuntu about drivers and it installed them. Chose TwinView and have dual head. Very quick and easy. 

The hardest part was fitting the low profile adapter things - needed to find some suitable tools!

In the end I bought a brand new HDMI to DVI cable. I was getting confused with all the different types of adapters which I found, so just bought a new cable for £6 or so.

Thanks again - really appreciate your help. 

Cheers

Ian

---

### Post by cascade9 on 2011-02-12
Great to hear it all worked out easily (well, apart from the tools anyway). 

Thanks for the feedback ;) 

BTW, it would be a good idea to mark this thread 'solved'

---

