---
title: "First Linux Geared Build (Few Questions)"
date: 2011-06-11
forum: Hardware
---

### Post by TheParadox on 2011-06-11
Hello Everyone. I am going to do my first build geared towards linux, more specifically the Ubuntu distro as the community support is fantastic. I am going with AMD mainly due to price; I am planning on getting a AMD Phenom II X4 965 as its plenty of performance and rather cheap now. Another reason is the bulldozer processors (8 Core) are expected in July and I would be upgrading once the price took a drop or two. My main question is who has a AM3+ board and what is the best one that is fully supported by ubuntu? Also what are some things to watch out for and look for when building a rig based around Ubuntu?

CPU: [http://www.newegg.com/Product/Product.aspx?Item=N82E16819103727]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103727")

Thanks

---

### Post by Joe of loath on 2011-06-11
[http://www.scan.co.uk/products/msi-870-c45-amd-770-s-am3-pci-e-20-%28x16%29-ddr3-1600%28oc%29-sata-3gb-s-sata-raid-atx](http://www.scan.co.uk/products/msi-870-c45-amd-770-s-am3-pci-e-20-%28x16%29-ddr3-1600%28oc%29-sata-3gb-s-sata-raid-atx)

The only thing to look for really is the video card, nvidia cards run better than ATI ones for gaming.

---

### Post by TheParadox on 2011-06-11
I don't think thats a AM3+ board which has the extra pin for the upcoming bulldozer CPU. Anyways I just recently found out ATI came out with drivers for linux. (Been out of the scene for awhile).

---

### Post by Joe of loath on 2011-06-11
Whoops, guess it's not. I thought it was when I ordered it :p

ATI has drivers, but they're sub-standard performance wise compared to the nVidia ones.

---

### Post by TheParadox on 2011-06-11
Awh. What does your setup look like? And do you have any problems? If so what? Also what would you do again if you had a chance. Thanks for your time. Just want to do this right the first time.

---

### Post by Joe of loath on 2011-06-12
[https://secure.scan.co.uk/aspnet/Shop/SavedBasket/Show.aspx?id=599084edb9ee46d69c651b9442e18ffe](https://secure.scan.co.uk/aspnet/Shop/SavedBasket/Show.aspx?id=599084edb9ee46d69c651b9442e18ffe)

Was £430, but some of the parts are discontinued. Only problem is that it doesn't shut down automatically, which I believe is a problem with the kernel in 10.04, since the RT kernel I installed for audio work is working fine. IMHO this is the perfect build for us (it's the family dekstop), so I wouldn't change anything. Maybe better fans? :lol:

---

### Post by Yellow Pasque on 2011-06-12
I would opt for the Phenom 955, since it's $20 cheaper ($30 with promo code at newegg). Making the 955 as fast as the 965 is probably as easy as raising the CPU multiplier.

---

### Post by TheParadox on 2011-06-12
> **Temüjin said:**
> I would opt for the Phenom 955, since it's $20 cheaper ($30 with promo code at newegg). Making the 955 as fast as the 965 is probably as easy as raising the CPU multiplier.

Yeah good idea. I saw that. So does ANYONE have a AM3+ board and can they comment on it?

---

### Post by cascade9 on 2011-06-13
> **Joe of loath said:**
> [http://www.scan.co.uk/products/msi-870-c45-amd-770-s-am3-pci-e-20-%28x16%29-ddr3-1600%28oc%29-sata-3gb-s-sata-raid-atx]("http://www.scan.co.uk/products/msi-870-c45-amd-770-s-am3-pci-e-20-%28x16%29-ddr3-1600%28oc%29-sata-3gb-s-sata-raid-atx")

The only thing to look for really is the video card, nvidia cards run better than ATI ones for gaming.

MSI should have got in some trouble over the "870-C45" IMO. Its a very misleading name, using the old 770 chipset but named as though is got the newer 870 chipset. 

For any given price point, ATI/AMD and nVidia GPUs are very close in performance. 

> **TheParadox said:**
> Yeah good idea. I saw that. So does ANYONE have a AM3+ board and can they comment on it?

Never owned one, but I recent built a Gigabyte GA-78LMT-S2P for a friend. Seemed pretty much the same as the AM2/AM3 AMD 760G gigabyte boards I've seen in tha past, apart from the black CPU socket. 

Dont get one, or any other 7XX/SB7XX boards, even if it is 'AM3+'. The SB7XX limit of SATAII (3Gb/s) alone will be annoying in the future. The 8XX/SB850 (and 9XX/SB950) chipsets have SATAIII (6Gb/s). 

So far none of the 990FX/990X/970 baords are on sale here as far as I know, and if I was planning on getting a AM3 CPU now then uprading to bulldozer when it comes out, I'd be getting a 9XX board for sure.

---

### Post by Joe of loath on 2011-06-13
> **cascade9 said:**
> MSI should have got in some trouble over the "870-C45" IMO. Its a very misleading name, using the old 770 chipset but named as though is got the newer 870 chipset. 

It's actually got the 870 chipset in, the website is wrong. There's a big 'AMD 870 chispet' logo on the front of the box :D

---

### Post by cascade9 on 2011-06-13
> **Joe of loath said:**
> It's actually got the 870 chipset in, the website is wrong. There's a big 'AMD 870 chispet' logo on the front of the box :D

You believe a logo? 

I klnow I've seen areview of the 870-C45, and they pointed out the same thing I did, its not an 870 chipset. IIRC they only realised that because they were planning on using the SATAIII ports from SB850 southbridge, but found that the board only had SATAII ports thanks to the SB710 southbridge.

*edit- I cant be sure exactly when it happened, but there are MSI 870-C45s without the 'AMD 870 Chipset' logo. The current box is like that- 

[http://www.msi.com/product/mb/870-C45.html](http://www.msi.com/product/mb/870-C45.html)

Considering that I've seen 870-C45 V2 boxes, which are also missing the logo, I'd say that the it was the earl boxes with the misleading "870 Chipset" logo.

---

### Post by Joe of loath on 2011-06-13
I assumed they'd be prosecuted for false advertisement if it didn't have inside what is said on the box. 

If you're correct (I'll do an lspci on the desktop later), I'm going to email MSI and see if I can get any free stuff.

---

### Post by TheParadox on 2011-06-18
> **cascade9 said:**
> MSI should have got in some trouble over the "870-C45" IMO. Its a very misleading name, using the old 770 chipset but named as though is got the newer 870 chipset. 

For any given price point, ATI/AMD and nVidia GPUs are very close in performance. 



Never owned one, but I recent built a Gigabyte GA-78LMT-S2P for a friend. Seemed pretty much the same as the AM2/AM3 AMD 760G gigabyte boards I've seen in tha past, apart from the black CPU socket. 

Dont get one, or any other 7XX/SB7XX boards, even if it is 'AM3+'. The SB7XX limit of SATAII (3Gb/s) alone will be annoying in the future. The 8XX/SB850 (and 9XX/SB950) chipsets have SATAIII (6Gb/s). 

So far none of the 990FX/990X/970 baords are on sale here as far as I know, and if I was planning on getting a AM3 CPU now then uprading to bulldozer when it comes out, I'd be getting a 9XX board for sure.
Thanks for the info. Sorry I was MIA. Got busy. Im still looking into building something affordable. I mean sure I have the cash to blow 2k on a rig but in this economy thats not exactly a smart thing to do, so trying to figure out my best option to build something midline thats somewhat futureproof.

---

### Post by Yellow Pasque on 2011-06-18
Unfortunately, I don't know if you're going to find a lot of hands-on Linux experience on AM3+ mobos. Looking at the specs/chipsets/price of this board, I can't think of a reason not to like it: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813128510](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128510)

---

### Post by cascade9 on 2011-06-19
> **TheParadox said:**
> Thanks for the info. Sorry I was MIA. Got busy. Im still looking into building something affordable. I mean sure I have the cash to blow 2k on a rig but in this economy thats not exactly a smart thing to do, so trying to figure out my best option to build something midline thats somewhat futureproof.

A 990X board (like Temüjin linked above) is only going to be about $50 more than a 870 board. Well worth the extra $$$  if you are looking for futureproof, and shouldnt be enough to change an affordable build to unaffordable....

---

### Post by TheParadox on 2011-06-19
> **Temüjin said:**
> Unfortunately, I don't know if you're going to find a lot of hands-on Linux experience on AM3+ mobos. Looking at the specs/chipsets/price of this board, I can't think of a reason not to like it: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813128510](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128510)

Thanks buddy. That looks absolutely fantastic. I love gigabyte. I heard its very compatible with *nix too. :popcorn:

---

