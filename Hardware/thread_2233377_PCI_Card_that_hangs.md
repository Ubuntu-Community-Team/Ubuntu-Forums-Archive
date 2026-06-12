---
title: "PCI Card that hangs"
date: 2014-07-08
forum: Hardware
---

### Post by Sylvain_Prevost on 2014-07-08
Hey all,

I have this PCI Card that whenever it's in the system Ubuntu hangs. Linux doesn't like this pci card since even in Debian it crashes. I am trying to blacklist this pci card but how can I find out with lspci when Ubuntu crashes.

When the card is removed from the system it works fine..

I checked all of the log files and I cannot see it.. I even tried to boot into the safe mode and even added some parameters and it still won't boot..

Where specifically in the log files that I should be looking in order to find what is the cards name?

---

### Post by Vladlenin5000 on 2014-07-08
Hi, welcome.

Do you know at least what that card is for?
And does it really hang or crashes (two different situations) or... in a OS session -or- it doesn't even let you boot?

---

### Post by Sylvain_Prevost on 2014-07-08
The pci card is kinda like a capture card for a camera..

I will make a video of Ubuntu booting with the card in it.

It doesn't let me boot at all. it gives me a kernel crash..

---

### Post by Vladlenin5000 on 2014-07-08
> **Sylvain_Prevost said:**
> It doesn't let me boot at all. it gives me a kernel crash..

So it does the POST, at least. Getting error messages from the OS means the BIOS already released control to the OS. I was afraid you weren't even getting to that point in which case either a BIOS update would solve it or you couldn't use that card on that PC.

Your case is weird and rare but certainly not unheard. 
At the moment I have no useful suggestions but I would try booting a live session with the card inserted just to see what happens.

---

### Post by Sylvain_Prevost on 2014-07-08
that pci card does the same thing on several motherboards.. it's not the bios... it even does it on a brand new Dell

---

### Post by Vladlenin5000 on 2014-07-08
So... Do you really need it? If not just ditch it as it seems to be a very bad piece of s... hardware.

---

### Post by tgalati4 on 2014-07-08
If your PCI card has a short in it--like a fried amplifier, then it will draw too much current and not allow the machine to boot.  Put your finger on the chips.  If any are too hot to keep your finger on, then you have found the problem.  Linux expects perfect hardware.  Log files would not provide useful information in this case.  If your card crashes more than one motherboard, I think you can conclude that the card is bad.

---

### Post by Sylvain_Prevost on 2014-07-08
we have over 100's of those cards and it does the exact same thing on each of them. yes I need it to be installed..

it boots into windows 7 with no problems.. just Linux that has issues with.

---

### Post by tgalati4 on 2014-07-08
Perhaps you need to blacklist a standard video driver that is being loaded.  It will be tricky to figure out what this video driver is.  What is the make and model of the PCI card?

For instance, if this video card has firewire (1394) in it, perhaps that is causing the problem.  You can blacklist the firewire portion:  [https://help.ubuntu.com/community/FireWire/DigitalAudio/OlderReleases](https://help.ubuntu.com/community/FireWire/DigitalAudio/OlderReleases)

---

### Post by Sylvain_Prevost on 2014-07-08
no firewire in any kind.. the grabber card which it's called is made by active silicon. we have a pci and a pci-x version of it.. the pci-x version has no problem in linux so I may connect the pci-x and run lspci and figure out what linux detects as in..

---

### Post by Sylvain_Prevost on 2014-07-09
nope the pci-x version of the same card does the same thing..

---

### Post by tgalati4 on 2014-07-09
Which specific card is it?  [http://www.activesilicon.com/products_fg_lfg.htm](http://www.activesilicon.com/products_fg_lfg.htm)

The website says it supports Linux.  I would send an email to their technical support.

---

