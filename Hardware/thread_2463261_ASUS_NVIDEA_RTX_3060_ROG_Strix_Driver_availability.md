---
title: "ASUS NVIDEA RTX 3060 ROG Strix: Driver availability"
date: 2021-06-07
forum: Hardware
---

### Post by makem2 on 2021-06-07
Is there a forum for GPU compatibility? I cannot find one.

If not does anyone know if any available Linux drivers work?

[https://linuxconfig.org/install-the-latest-nvidia-linux-driver](https://linuxconfig.org/install-the-latest-nvidia-linux-driver)

Appears to suggest it may/might.

---

### Post by Bashing-om on 2021-06-07
makem2; Hello -

This is ubuntu - we do have a close working relationship with Nvidia.

Please heed the blog's caveat; in addition, Nvidia also advises:
> 
Note that many Linux distributions provide their own packages of the NVIDIA Linux Graphics Driver in the distribution's native package management format. This may interact better with the rest of your distribution's framework, and you may want to use this rather than NVIDIA's official package.


With that said - the system is some kind of smart to choose the correct driver for a particular card:
```

sudo ubuntu-drivers devices #To see all the devices that need drivers (list the proprietary video drivers available for your graphic card).
sudo ubuntu-drivers list # to see all available drivers. These commands take a while to run.
sudo ubuntu-drivers autoinstall #to install the standard available proprietary video driver; This will install the latest proprietary video driver.

```

Furthermore: *IF* you have bleeding edge hardware - we have a Trusted PPA that maintains the latest (and earlier updated) drivers as provided by Nvidia
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
That provides the Fresh drivers from upstream.

[INDENT]let the system do the heavy lifting
[/INDENT]

---

### Post by makem2 on 2021-06-07
Thank you

---

### Post by Bashing-om on 2021-06-07
makem2 - :D

Most Welcome

[INDENT]help is what we do
[/INDENT]

---

### Post by makem2 on 2021-06-12
> **Bashing-om said:**
> makem2 - :D

Most Welcome[INDENT]help is what we do
[/INDENT]


I have been miss-sold the Nvidia 3060 card and the supplier can only supply the following two cards as a replacement.

[COLOR=#2F5496]ZT-A30600E-10M

[https://www.zotac.com/us/product/graphics_card/zotac-gaming-geforce-rtx-3060-twin-edge](https://www.zotac.com/us/product/graphics_card/zotac-gaming-geforce-rtx-3060-twin-edge)
[/COLOR]
[COLOR=#2F5496]Palit DUAL

[https://www.palit.com/palit/vgapro.php?id=4089&lang=en](https://www.palit.com/palit/vgapro.php?id=4089&lang=en)

[/COLOR]Would those cards be inferior to the Asus card?

[h=2][COLOR=#222222]The company Pcsystems say that Nvidia and Linux don't work very well together and AMD do work well.[/COLOR][/h]
Is he right generally?

---

### Post by linuux on 2021-09-20
Did you pick a card?  I don't know if you are still following this thread but there's some youtube video reviewers that compared many 3060s/3060 Tis etc.

I think they are all pretty much the same at stock but start to differ/vary in performance when you push them, i.e. overclock them.  

I would grade the cards you're comparing this way:   Palit < Zotac < Asus

In saying that, the card shortage and prices are so bad, I would choose what's available and what's cheapest, if you have a choice between cards.

Ubuntu includes the Nvidia driver in their repo - I believe you need to enable the non-free repository and choose 'Additional Drivers' - then chose whatever driver you want enabled.  I don't know if you need to reboot/restart but I would.  

It's been a while - and I don't currently have Ubuntu installed on my computer (it's old) but I did on a previous computer.  :)  

A web search on Ubuntu and Nvidia drivers - will instruct you to do all this - I believe it's accurate.

---

### Post by abbyjace on 2021-09-23
[COLOR=#000000]Did you pick a card? [/COLOR]

---

