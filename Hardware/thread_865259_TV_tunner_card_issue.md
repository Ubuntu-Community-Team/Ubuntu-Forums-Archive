---
title: "TV tunner card issue"
date: 2008-07-20
forum: Hardware
---

### Post by pundip on 2008-07-20
I have a Pinnacle Systems tv tunner card chipset SAA7134HL and I am trying to get it to work in ubuntu 8.04. I suppose the first step would be to determine if this chipset is supported by linux or not. Can anybody help me determine if this tv tunner card can be used in ubuntu or not

---

### Post by pundip on 2008-07-20
just had another quick look. It seems dmesg and lspci seem to recognise the card. Any advice on how to get it to work?

dmesg:
[  123.512774] saa7134[0]: found at 0000:01:0a.0, rev: 1, irq: 20, latency: 64, mmio: 0xf7effc00
[  123.512786] saa7134[0]: subsystem: 11bd:002b, board: Pinnacle PCTV Stereo (saa7134) [card=26,autodetected]
[  123.512815] saa7134[0]: board init: gpio is 0

lspci:
01:0a.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)

---

