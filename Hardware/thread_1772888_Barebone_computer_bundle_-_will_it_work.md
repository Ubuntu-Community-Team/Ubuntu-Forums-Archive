---
title: "Barebone computer bundle - will it work?"
date: 2011-06-01
forum: Hardware
---

### Post by stevejm22 on 2011-06-01
Hi,
 
I have been using Ubuntu for a while now, and want to build a new computer using a barebones bundle on sale here:
 
[http://www.novatech.co.uk/novatech/prods/barebones/Novatech/BB-8404N.html](http://www.novatech.co.uk/novatech/prods/barebones/Novatech/BB-8404N.html)
 
Here are some of the details:
 
Processor
Clockspeed 3.20Ghz 
Manufacturer AMD 
Description AMD Quad Core Phenom II X4 840 
Cache 2MB 
 
Memory
Speed 1333Mhz 
Description 2 x 2GB DDR3 1333Mhz Memory 
 
Motherboard
Chipset AMD 760G + SB710 
Description Onboard ATI Radeon 3000 
 
 
I have installed Ubuntu before, but I would like to know if anybody can spot any hardware in this bundle that will cause an issue. I am thinking particularly of the onboard graphics (I don't particularly want to spend more money on a separate graphics card).
 
Have asked the company selling for advice, but they don't support Ubuntu...(odd for a company selling computers without an OS?)
 
I also want to get a bluray burner. I know not everyone likes the idea, but from a compatibility point of view only, will this be ok?
 
Thanks in advance,
 
Steve

---

### Post by coffeecat on 2011-06-01
Hi, and welcome to the forum.

I have an Asus M4A78LT-M motherboard which has the same AMD 760G/SB710 chipset and onboard ATI Radeon 3000 graphics. I was not able to get a working GUI with the live Natty/11.04 CD with the onboard graphics, although to be honest I didn't try very hard as I intended to put a PCIe graphics card in anyway.

That somewhat surprised me as the default open source ATI driver is very capable with the 4*** series Radeon chipsets I've tried it with and I've read that the 3*** series should be OK. If I had tried with some boot options, I'm sure I could have got something though.

I can understand you not wanting to spend money on a separate graphics card, but if you were prepared to, it's much better to have a dedicated GPU with its own RAM. 

Sorry I can't help with Blu-Ray.

---

### Post by stevejm22 on 2011-06-03
Thanks for your help.

I want a computer that will be able to easily handle HD video (playing & editing), with a big HD for storage and plenty of RAM.  I'm not that interested in gaming, so I don't suppose I need the best graphics card in the world, as long as it copes with the video.

Can you recommend hardware that will do the job without breaking the bank?

Thanks again.

Steve

---

### Post by coffeecat on 2011-06-03
> **stevejm22 said:**
> Thanks for your help.

I want a computer that will be able to easily handle HD video (playing & editing), with a big HD for storage and plenty of RAM.  I'm not that interested in gaming, so I don't suppose I need the best graphics card in the world, as long as it copes with the video.

Can you recommend hardware that will do the job without breaking the bank?

Thanks again.

Steve

See what others say, but that barebones seems good - you just need a decent PCIe video card. And it just so happens I can recommend two which are  modestly priced. I have both. Both cope with HD video just fine and with compiz/3d/Unity.

Number one is ATI Radeon HD4350. It works out of the box with the open source driver, so nothing extra to install. This is the one I have:

[http://www.amazon.co.uk/gp/product/B001U3U70O/ref=pd_lpo_k2_dp_sr_2?pf_rd_p=103612307&pf_rd_s=lpo-top-stripe&pf_rd_t=201&pf_rd_i=B001R5IJSC&pf_rd_m=A3P5ROKL5A1OLE&pf_rd_r=02CM9PDMAS60Y1MNHKK0](http://www.amazon.co.uk/gp/product/B001U3U70O/ref=pd_lpo_k2_dp_sr_2?pf_rd_p=103612307&pf_rd_s=lpo-top-stripe&pf_rd_t=201&pf_rd_i=B001R5IJSC&pf_rd_m=A3P5ROKL5A1OLE&pf_rd_r=02CM9PDMAS60Y1MNHKK0)

I had a look on the Novatech site but they don't have any HD4350's but if you look around you can find ones slightly cheaper, such as this Asus (also passively cooled):

[http://www.ebuyer.com/product/169294](http://www.ebuyer.com/product/169294)

If you want nvidia, then the GeForce 8400GS with the proprietary driver should suit your needs. They have a selection on the Novatech site, in the same price range:

[http://www.novatech.co.uk/novatech/prods/components/nvidiageforcegraphicscards/nvidia8000series/](http://www.novatech.co.uk/novatech/prods/components/nvidiageforcegraphicscards/nvidia8000series/)

These are modest graphics cards by gamer's standards but should be adequate for what you want.

By the way, since I posted last I came across a thread where someone did have a resolution problem with onboard ATI 3000 graphics, but had at least got it working. You might want to do a forum search.

---

