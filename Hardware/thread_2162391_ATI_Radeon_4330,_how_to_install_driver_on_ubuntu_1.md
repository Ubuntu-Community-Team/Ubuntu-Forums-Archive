---
title: "ATI Radeon 4330, how to install driver on ubuntu 12.04"
date: 2013-07-14
forum: Hardware
---

### Post by kamkarot on 2013-07-14
Hello, I have just downloaded ubuntu 12.04 (I tried 13.04 many times but it never worked [errno 5 was always the answer]) onto my old MSI laptop cx700 { [http://www.msi.com/product/nb/CX700.html#?div=Specification](http://www.msi.com/product/nb/CX700.html#?div=Specification) } and I am having trouble figuring out how to install the driver for my graphics card. Although, I am totally unsure if I should even install a driver for it; maybe Ubuntu has its own version of driver?

I downloaded the linux driver from AMD themselves and 7zip but have nothing else on the computer as of now. Any help would be greatly appreciated!


-Kamkarot

---

### Post by Sarcastic Cows on 2013-07-14
You may need Legacy drivers. To be honest, I'd just stick with the open source drivers.

---

### Post by Bashing-om on 2013-07-14
Sarcastic Cows; My Welcome to the forum .

Here is the situation:
> 

IF its an HD 2x/3x/4x then you are out of luck as AMD announced <last> summer that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.10 uses X-server v1.13.
That's because, starting with Ubuntu 12.04.2, the X-server version was updated to a newer version that is now incompatible with the HD 2x/3x/4x series AMD cards.
(Mark Phelps)
This is the suggested option to pursue:

If you want to use the proprietary AMD/ATI driver, install Ubuntu 12.04.1: 
[http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)
This is a Long Term Support version that will have support until 2017 !

Else: In most cases the provided open source driver performs admirably .

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

