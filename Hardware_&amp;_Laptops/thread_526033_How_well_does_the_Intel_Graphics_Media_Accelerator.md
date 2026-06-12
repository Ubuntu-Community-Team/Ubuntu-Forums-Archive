---
title: "How well does the Intel Graphics Media Accelerator x3100 work with Compiz Fusion?"
date: 2007-08-15
forum: Hardware &amp; Laptops
---

### Post by Espreon on 2007-08-15
I was looking at one of those Dell Laptops with Ubuntu, they are great but only one flaw the graphics card is a piece of crap integrated chip. They used to sell a Lappy with Ubuntu that had the option of having an Nvidia Card. But the Q is that will the card work well with Compiz Fusion, meaning it won;t be slower than a slug, and it will be compatible woth EVERYTHING like water,lightning and so on.
If not is there a Dell Laptop that has a wireless card that works with Linux and has a decent graphics card that can easily work with CF and would be fully compatible (meaning no Ndiswrapper required, Ndiswrapper can be sort of bitchy and with the card it would hafta be fully compatible with CF) If that is not possible then list a Dell Laptop with a graphics card that is what I desire and the wireless card works well with Ndiswrapper. 

I hafta have a lappy since My household has a wireless network and I would hafta pay extra to hook up via ethernet.

---

### Post by benanzo on 2007-08-15
I have a mobo with the Intel GMA965 chipset and X3000 GPU and it works flawless out-of-the-box with Compiz Fusion.  All plugins work really well.  Heck, the Intel GMA950 on my MacBook does Compiz flawlessly, so there's your answer.

---

### Post by Espreon on 2007-08-15
grand, thanx, is CF slow on that integrated crap?

---

### Post by arikperl on 2007-08-22
hi, for me (dell d630 with x3100, 965 cihipset with 4965 wireless),
compiz and beryl work only when using a backport of the intel driver (not the stable on offered by ubuntu repositories), and the 4965 wireless only work with ndiswrapper (allthough there seem to be a way to build the linux driver from intel, but not linux driver out of the box), allthogh it works preety well with ndiswrapper.

compiz and beryl work realy well with the x3100 card (if talking about performance), although I had troubles getting compiz-fusion to work (but i gave it only ten minutes), and for example the water plugin dosn't work for me.

I guess when gusty comes ot (2 month fom now i believe) the probems will be fixed (intel 2.0 driver for x3100 and i think a new version of  Xorg). hope it helps you.

---

