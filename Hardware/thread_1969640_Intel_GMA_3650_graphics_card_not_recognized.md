---
title: "Intel GMA 3650 graphics card not recognized"
date: 2012-04-30
forum: Hardware
---

### Post by afp2001 on 2012-04-30
I have an MSI U180 (specs here: [http://www.msi.com/product/nb/U180.html#/?div=Specification](http://www.msi.com/product/nb/U180.html#/?div=Specification)). When I bought it in March, I installed a dual boot of Ubuntu 11.10 alongside Windows 7 starter. Ubuntu could not detect the screen, and the resolution was therefore off (in Displays, the only display was "Unknown"). 

I'm now testing Ubuntu 12.04 off a live USB and getting a stretched screen again. In the Displays page, now the resolution is 600x800, the "rotation" is Normal, and the launcher placement says "All Displays". All the dropdown menus have no choices available.

As far as I can tell, this is a driver issue - and it seems there is no driver for the graphics card, an Intel GMA 3650. Is this a correct diagnosis? If so, how do I fix it? Is there a linux or ubuntu driver for this graphics card? And how do I install a new driver? I find this hard to believe - this is such a mainstream computer...

Thanks in advance.

---

### Post by g_marotta on 2012-04-30
Yes, I've got the same question, you've just anticipated me. From what I can see around googling, it seems your diagnosis is correct, there is still no driver around.

---

### Post by afp2001 on 2012-04-30
Is there a way around the lack of driver? Is there a way to force the screen to a specific solution, even if the graphics card isn't recognized? Would an older version of Ubuntu make this easier?

---

### Post by graeme1950 on 2012-05-04
Just for information - I've just purchased a Shuttle XS36V and getting results for display resolution of 1024 x 768 or 800 x 600 so anyone thinking of buying this shuttle will not get the full graphics capability. I'm running Lubuntu 12.04LTS and tried with Ubuntu 12.04LTS both give same results.
Note:The XS35V uses the Mobility Radeon HD7410M graphics which is the same animal as the XS36V apart from graphics - by the looks of things. 

I intend to use this XS36V to run openbravopos with a touch screen monitor as a till system so the resolution needed is 800 x 600, so I'm hoping I don't find other limitations.. Already know about the Wireless network issues.. but this is shuttle is running on normal ethernet port.. Currently I have openbravopos running on a windows XP box and want Lubuntu as a replacement for XP to carry the openbravopos...

---

### Post by titi lbare on 2012-08-08
Hi!
I have the same problem with this graphics card on an asus with ubuntu 12.04. It probably cause some problems on the X server so I can't use at least a program (paraview) which tell me it can't "connect to X server", when I try to use it.
Did you find a solution since you made your posts? 
Thanks for any answer

---

### Post by OriTheEep on 2012-08-08
> **graeme1950 said:**
> The [Shuttle]XS35V uses the Mobility Radeon HD7410M graphics which is the same animal as the XS36V apart from graphics

I intend to get one of these wee beesties myself, although I'm actually looking at the XS35GTV2. The XS36V, from the spec sheet, actually uses the Intel GMA 3650 so a definite no-hoper. The XS35GTV2 uses a "Built-in Nvidia next generation ION" which is more hopeful but unhelpfully unspecific.

You would have thought that a manufacturer who sells machines without an OS, particularly at the budget end of things, would take the care to ensure that some flavour of Linux was at least a satisfactory option.

---

### Post by hads on 2012-08-12
The XS35GTV2 works fine.

---

