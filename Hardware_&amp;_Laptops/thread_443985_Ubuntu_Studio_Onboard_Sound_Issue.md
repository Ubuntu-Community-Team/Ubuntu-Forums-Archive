---
title: "Ubuntu Studio: Onboard Sound Issue"
date: 2007-05-14
forum: Hardware &amp; Laptops
---

### Post by bluetang on 2007-05-14
First: is there a better place to post this?

I'm the happy owner a new home built workstation:
Asus P5B Deluxe
Core 2 Duo 6400
2GB
7600 GT 512mb
M-Audio Audiophile 2496

The onboard sound works just fine. I'm using it right now to listen to some dub mixes by Adrian Sherwood. My issue is that I'm coming from making music on the windows side with HomeStudio ect. So I have a Audiophile 2496. 

It shows up in the Device Manager  under PCI devices as > ICE1712 [Envy24] PCI Multi-Channel I/O Controller

```
asoundconf list
Names of available sound cards:
Intel
```

My bad for buying a mobo with onboard audio. I was drawn to the bonus I/Os.


I now want to make music using Ubuntu studio. My guess is that the ICE1712 will do better Full duplex than the Intel chip set. So far Hydrogen sounds crappy with Intel sound. Can set the system up to be able to toggle between both? 

What are my best options? If I have to choose one, it will be the ICE1712. I tried turning off onboard audio in the bios during install of Ubuntu Studio. The ICE1712 (audiophile 2496) wasn't recognized.

Thanks.

---

### Post by Patrick K on 2007-05-17
I have the same card. I disabled the onboard in Bios to get the card working. Although, it seems both can be used. I don't have the problem you have (I have others). The only thing I can suggest is spending some time at the ALSA site. I seem to recall instructions on setting up the card but I have been to so many pages there I can't help with which one (they are all pretty much a blur). Try both WIKIs. You might find what you need.

---

