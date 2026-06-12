---
title: "Graphics card recommendation"
date: 2010-05-26
forum: Hardware
---

### Post by karmic-koala on 2010-05-26
Hello,

I am shopping for a good graphics card for my PC at work. Any recommendations on cards that support dual monitors and work flawlessly on Ubuntu Desktop?

A little bird told me NVIDIA and Ubuntu don't get along well, is that true?

---

### Post by jean noel on 2010-05-26
> **karmic-koala said:**
> Hello,

I am shopping for a good graphics card for my PC at work. Any recommendations on cards that support dual monitors and work flawlessly on Ubuntu Desktop?

A little bird told me NVIDIA and Ubuntu don't get along well, is that true?

I do not know about new drivers for amd/ati video cards, but I would recommend nvidia. As for models, I do not know, as i am using an old fx5500.
PS my previous one was a Radeon 9550.
Regards

---

### Post by karmic-koala on 2010-05-26
Thanks for that. Looks decent, will have a look.

---

### Post by SlugSlug on 2010-05-26
I use a 
GeForce 9600 GT

it plays nice with ubutnu 1080p files, and runs my Battlefield2 nice (slight overkill ;))

hammered cyris when I tested that

---

### Post by karmic-koala on 2010-05-26
Come to think of it I already have an inbuilt graphics chip, would installing a dual output graphics card allow me to run 3 monitors or am i just being too fussy?

---

### Post by Vincentlaborant on 2010-05-26
Drivers depend up 1 thing:

Do you want to use the proprietary drivers of Nvidea or not? The proprietary driver works good/ excellent.

Last time I checked I had more trouble with ATI cards then Nvidea cards.

---

### Post by cascade9 on 2010-05-26
> **karmic-koala said:**
> Hello,

I am shopping for a good graphics card for my PC at work. Any recommendations on cards that support dual monitors and work flawlessly on Ubuntu Desktop?

A little bird told me NVIDIA and Ubuntu don't get along well, is that true?

Are you just after a card for dual monitors, or will you be gaming and/or watching HD video as well? Virtually any nVidia card with dual monitor outputs should work (though I'd avoid anything older then geforce 2). For gaming, the more power, the better..and for video/HD, a 8XXX series or newer card is the way to go. 

Probably a good idea to check what cards your motherboard can use as well, almost everything is fine with PCI card (but PCI is slower, and the cards more expensive than for the other slots). AGP is the 'old' video card specific slot, and its hard to find the newer nvidia cards in AGP (the last cards nvidia made for AGP was the old 7XXX series). The cards are still more expensive than the newer PCIe slot cards. 

At the moment, nVidia cards have better support than ATI. When the ATI opensoruce drivers mature a bit more, that may very well change. 

You *might* be able to run triple monitors with an nvidia card + the onboard video, but that is going to much harder to setup, if it is possible.

---

### Post by Keith_K on 2010-05-26
> **karmic-koala said:**
> Come to think of it I already have an inbuilt graphics chip, would installing a dual output graphics card allow me to run 3 monitors or am i just being too fussy?
you'll probably have to select between the onboard card or the agp card in your bios so more than likely not.
I'm using an ATI Radeon HD 2400 Pro and it works perfectly with dual monitors in 9.10 with the ATI drivers and compiz. 
I've had less luck on my old machine that has a nvidia GeForce MX 420, which is obsolete, but using the Nvidia priority drivers put it into vga mode. But like I said, this is an old card.

---

