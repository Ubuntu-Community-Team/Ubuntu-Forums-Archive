---
title: "[SOLVED] New (second-hand) soundcard not detected"
date: 2008-03-22
forum: Hardware &amp; Laptops
---

### Post by matrooswolf on 2008-03-22
Hi,
my son broke his headphone plug in the on-board soundcard. We tried to get it out, but no success.  
So I got an old pci soundcard from a friend and installed it (I think it is a soundblaster from creative, but I am not sure).  
How do I get Ubuntu to detect the soundcard and to play from that card instead of the broken on-board soundcard?

---

### Post by teaker1s on 2008-03-22
firstly you will need to disable  on board sound in bios. then if you can't find any useful info for your model in ubuntu community docs /ubuntu wiki or google  then
terminal ```
lspci 
```and see the vendor and product id which will aid in finding a solution.

If your not sure then post the model number and lspci output. if you do not know the model then post any numbers printed on card as they tie in with fcc codes

---

### Post by matrooswolf on 2008-03-23
Thanks for your reply,

I looked around in the Bios, but I'm not very familiar with it.

to disable the onboard sound do I have to disable this: VIA AC97 Audio?  It is set to Auto now. And has this something to do with it?  AC97 Speaker At POST?  But that one is set to Disabled.  

After that I'll open the computer and see if I can find any numbers on the card.  I'll keep you posted.

---

### Post by teaker1s on 2008-03-23
yes disable ac97 audio, it's the on board sound. :guitar:

---

### Post by matrooswolf on 2008-03-24
So I've disabled the onboard sound.

The soundcard is a Creative Labs CT4810.

The output of ```
lspci
``` gives 
```
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:0a.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface
00:0c.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

```

Does that mean the card is not recognized?

---

### Post by matrooswolf on 2008-03-24
We have sound.

Apparently after disabling the on board sound, Ubuntu detected the PCI card, and everything is working perfectly.

Thanks for the advice!

---

### Post by teaker1s on 2008-03-24
:popcorn:

---

