---
title: "restricted-manager in Kubuntu Feisty?"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by madcow72 on 2007-04-25
I installed Kubuntu Feisty onto a friend's laptop, which has an ATI video card.  I wanted to install the ATI driver to get the card working, but am honestly unsure what model card it is.  (How do I probe that, by the way?  Commands like "lspci" do tell me that the card is ATI, but doesn't give a model number.  It may be a 4-5 year old card, judging by the look of the laptop.)

Installing the xorg-driver-fglrx and running the command ```
aticonfig --initial
``` and disabling composite breaks the X server when restarting.  So my questions are, 1) Why does restricted-manager seem to be missing from Kubuntu 7.04?  2) Should I download and compile the proprietary ATI driver to get things working correctly and if so, 3) How can I determine what the card is so I can download the correct driver?

Thanks for any help!

---

### Post by madcow72 on 2007-04-25
Okay, learned a little bit.  Nothing good.

I don't think the card actually has a numeric model number. ```
 lspci | grep ATI
```  tells me that the card is an ATI Radeon LM W6  (or something like that, unfortunately I don't have the laptop in front of me at the moment.)  By checking out the hardware section in System Settings, I realized that the card has 128MB RAM, which is quite decent, although I don't know that it's dedicated.  

I tried the earliest ATI binary (8.28.8 ) driver from the website, but it won't install.  The xorg-driver-fglrx breaks X (as I already mentioned), and the open-source Radeon driver does nothing.  No 3D rendering enabled with AIGLX enabled, and glxgears gives me ~180 fps.  Ouch!

Any suggestions?

---

