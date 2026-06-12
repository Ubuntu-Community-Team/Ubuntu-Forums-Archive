---
title: "what is the fastest/best video card that is pci express x16 spec 2.0 for ubuntu?"
date: 2016-07-30
forum: Hardware
---

### Post by craymore on 2016-07-30
what is the fastest/best video card that is pci express x16 *spec 2.0* for ubuntu?  that would be using ubuntu 14.04 and above.  

further i have two slots in my Optiplex 980 i believe and am curious if i can use two of those video cards for cpu enhancement and not just for specific applications like boinc.  

thanks

---

### Post by papibe on 2016-07-30
Hi craymore.

These days Nvidia is the brand of discrete cards that has better support on Linux/Ubuntu. However, if the card is too new, like out on the market recently, there are chances that the support could be spotty.

One safe way to choose your card is to see the documentation of the Nvidia driver which lists al supported cards. For instance, taking a look at the list, I think the GeForce GTX 780 could be one of the top ones (Ubuntu official Nvidia driver 340 on 14.04).

In order to see the list, install the nvidia driver on 14.04:
```
sudo apt-get install nvidia-340
```
I believe you can do the same with every Ubuntu version by doing:
```
sudo apt-get install nvidia-current
```
An the supported cards, are in the file:
```
/usr/share/doc/nvidia-340/README.txt.gz
```
As an alternative, you could get a newer driver from the Nvidia site. This may support newer cards, but there a a couple of inconveniences: (1) there's no official support, and you need to reinstall it every time you get a kernel upgrade.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by kyrithis on 2016-07-30
I concur with Papibe on most points. AMD cards are also a decent option if you're fairly savvy at re-working drivers, though those are about the only two brands with any real Linux support.

If you're looking for a card with guaranteed compatibility, I use an Nvidia GeForce GTX 660. It's able to play GTA 5 at 1080p with 50~60 FPS, though it's far from being brand new. This works extremely well for me on Ubuntu 16.04.

---

### Post by craymore on 2016-07-30
i have specific requirements for a 2.0 pci-express x16 card because my stupid computer is so old.  can anyone suggest the best card that would work on that specification that is both fast/good quality, and further hopefully (although optionally i am willing to get my hopes up) can be configured to supplement cpu processing power on need or on every possible scenario.  if there are only few applications that use it like boinc then i don't think its worth it because i don't use that.  if the entire system can use it then i'd be very pleased.   

thank you very much, both of you.

---

### Post by kyrithis on 2016-07-30
Ahh, PCI-e 2.0 spec? Your best bet would likely be Nvidia's GT series. I believe the best would probably be a GT 610 or 630, both use PCI-e 2.0 x16.

Also, as far as using cards for extra computing, I'm not sure that's possible without specially written programs and projects (Such as BOINC or GUIMiner for BTC). So, your only likely gain here would be the ability to play decently modern games.

Here's a Newegg link to a GT 610 card, it appears to be the rough best:
[http://www.newegg.com/Product/Product.aspx?Item=9SIA4UB1JA6642](http://www.newegg.com/Product/Product.aspx?Item=9SIA4UB1JA6642)


EDIT:That's a low profile card, I do suggest you shop around and find a  version that fits your form factor and meets your other requirements  such as power supply. If you send me a list of your hardware including  case size, I'll see if I can pick one for you.

---

### Post by Yellow Pasque on 2016-07-30
You do know that PCI-e is, for the most part, backwards compatible, right? A PCI-e 3.0 card should work fine, although its max bandwidth will be limited (which may or may not be noticeable in real world performance depending on what card you get).
Of greater concern to you is the power supply, especially if you want to install two GPU's. You're probably going to need to upgrade that unless you're looking at really low-end GPU's.

> further i have two slots in my Optiplex 980
Which version of the Optiplex 980 do you have? [http://www.dell.com/downloads/global/products/optix/en/optiplex-980-tech-guide.pdf](http://www.dell.com/downloads/global/products/optix/en/optiplex-980-tech-guide.pdf)

> am curious if i can use two of those video cards for cpu enhancement
Can you be more specific about "cpu enhancement" and why you need two GPU's?

---

