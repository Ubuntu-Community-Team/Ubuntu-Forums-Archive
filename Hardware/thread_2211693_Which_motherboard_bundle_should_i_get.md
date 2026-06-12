---
title: "Which motherboard bundle should i get?"
date: 2014-03-17
forum: Hardware
---

### Post by upa_bigtree on 2014-03-17
About a year ago my old trusty desktop had a catastrofic failure and pretty much commited suicide, frying most of its components! 

So a friend of mine threw together a cheap emergency system for me out of my remaining working parts and a few salvaged bits he had lying around! The result was not pretty but its got me by for the past year! Anyway, its performance is not great so ive decided its time to upgrade! Here is my current setup, please dont laugh!

* Case - CIT vantage black mid tower gaming case
* Motherboard - Asus P5RD2 TVM/S R1.01G
* CPU - Intel pentium D 2.80 Ghz (200x14.0) 2 CPU
* RAM - 2GB DDR2
* GFX - Radeon HD 6450 
* PSU - 500w
* OS - Ubuntu 13.10

I mostly use it for watching videos and playing abit of Minecraft, unfortunately it struggles with this! 
It will play most videos without any problems but HD files seem to be really choppy and unwatchable! It will also play Minecraft, but barely... i get an FPS of about 5-15 (average of about 10fps) playing vanilla with settings on low, but when things get busy (lots of lava and mobs) it drops off completely resulting in certain death!

All this fustrates me so im looking at upgrading with a motherboard bundle, but being a complete noob i havent got a clue about whats good or not, or if it will be compatable with Ubuntu! 
I would like to be able to watch HD videos flawlessly and also play a Heavily modded Minecraft, with texture packs / shaders etc at about 60-100 fps. I would also like to be able to capture gameplay but thats not too important if its gonna get too expensive!

I was looking at something like [this]("http://www.novatech.co.uk/products/motherboardbundles/mbb-41304g.html") 
or [this]("http://www.novatech.co.uk/products/motherboardbundles/mbb-63004b.html")

so i suppose my question is, 
* Are these any good for my needs? if so Which 1? if not, any suggestions with links will be appreciated!
* Also, if i upgrade will my GFX card be compatable (or worth keeping) and will i need a new PSU?

Many thanx in advance
Rob

---

### Post by Yellow Pasque on 2014-03-17
I would avoid the AMD bundle you link to like the plague because it's overpriced and Gigabyte's AMD 900-series boards have issues with IOMMU. Some people can work around it with boot options, but other people never figure it out or get everything (USB3, ethernet) to work concurrently. [http://ubuntuforums.org/showthread.php?t=2143433](http://ubuntuforums.org/showthread.php?t=2143433)

As for the Intel bundle, it looks okay, but I don't know too much about the mobo. That CPU is ideal because it's fast and has hyperthreading. It only leaves you with two options:
1) Spend less money on an equivalent Pentium CPU ( [http://www.novatech.co.uk/products/components/processors/intelceleronandpentium/bx80646g3430.html](http://www.novatech.co.uk/products/components/processors/intelceleronandpentium/bx80646g3430.html) ) and hope that two cores is enough for Minecraft
2) Spend more money for an actual quad core

> Also, if i upgrade will my GFX card be compatible (or worth keeping)
Compatible? Yes.
Worth keeping? That's something I would wait and see on. You can always try out the 6450 with the new system and upgrade to a GTX 750 Ti 2GB later: [http://www.novatech.co.uk/products/components/nvidiageforcegraphicscards/nvidiagtx750tiseries/n750titf2gd5oc.html](http://www.novatech.co.uk/products/components/nvidiageforcegraphicscards/nvidiagtx750tiseries/n750titf2gd5oc.html)

> and will i need a new PSU?
Probably not (assuming your PSU isn't a relic from the 2003/2004 days when systems drew more power on the 5V rail). Your new system will draw about as much (and probably less) power than your current one. Even if you put in a new GPU, 500W is more than enough assuming the new GPU isn't a power-guzzling monster.

One thing you may want to be aware of is that newer mobos want 8-pin CPU connectors and older PSU's only have a 4-pin connector, which may or may not be able to supply enough power to the CPU. That issue is easily remedied with a cheap adapter: [http://www.newegg.com/Product/Product.aspx?Item=N82E16812198003](http://www.newegg.com/Product/Product.aspx?Item=N82E16812198003)

---

### Post by upa_bigtree on 2014-03-17
Cheers for the info, as I'm going to give it a go myself an I'm a complete noob I'll take your advice an leave the amd! the links where just a rough guess on my budget but I would rather spend more and be covered for any future ideas so I'll prob go down the quad core route!

---

### Post by upa_bigtree on 2014-03-18
Hi, I've just found a used but working Asus P7P55D with an intel i5 1156 chip and cooling fan
Will this be a suitable setup for Ubuntu? And roughly how much is it worth second hand! (Don't wanna spend more than I need to!)

---

