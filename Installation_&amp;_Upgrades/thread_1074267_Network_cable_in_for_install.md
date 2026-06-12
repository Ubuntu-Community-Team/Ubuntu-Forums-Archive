---
title: "Network cable in for install?"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by Bucky Ball on 2009-02-19
Hi all,

Strange and elementary question perhaps, but ...

I have always installed Ubuntu with the ethernet cable plugged in. I am about to install on a brand new box I have built for my mother-in-law and this is going to have a wireless PCI card in it. I have a cable there, the PCI card there. Should I install the PCI card then install Ubuntu, plug the ethernet cable in and install Ubuntu or leave 'em both out and add the wireless card later or ...

... is there a norm? Couldn't find much info. Is it actually necessary to be online for the install? I'm thinking not ...

I'm thinking I might just put the wireless card in and install Ubuntu then get the card running once I'm up ...

---

### Post by mikewhatever on 2009-02-19
I think it's a good idea to connect the wireless card. Who knows, it might be recognized by the installer and just work. As for the cable, it doesn't matter really.

---

### Post by Bucky Ball on 2009-02-19
Thanks Mikewhatever. I was looking in the wrong places. It's all in the installation guide here:

[https://help.ubuntu.com/8.04/installation-guide/powerpc/index.html](https://help.ubuntu.com/8.04/installation-guide/powerpc/index.html)

If the device needs a proprietory driver, don't use it  for the install because the installer won't pick up the required wares for it. If there is a cable, plug it in. Is possible to install without connection but you will only get what is on the cd, not from the mirrors. You then set up the wireless device once you're up.

In my case, once I'd installed and booted into Ubuntu, the drivers were employed without me doing a thing, my home network was found (along with another one), I selected mine, was asked for the WEP key, and voila, there you go! Brilliant!

Congrats to all, things have changed a lot since I spent 6 months wrangling in Gutsy with my Broadcom card and gave up. Installed Hardy and the Broadcom card was up in 5 minutes too. Now, 7 months later, this!

The speed is not the greatest and I am not too far from the router, so that is a question mark, but at least it is working. Pays to spend 7 or 8 hours working out which card is going to work 'out of the box'.

\\:D/ :)

* Incidentally, the wireless PCI card is a TP-Link TL-wn651G with Hardy 8.04.2  Happy as a pig in ... only just installed so shouldn't speak too soon, see how things go but wireless was once the dreaded curse of the Ubuntu setup ...

---

