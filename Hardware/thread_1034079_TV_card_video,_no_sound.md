---
title: "TV card video, no sound"
date: 2009-01-07
forum: Hardware
---

### Post by neoTheCat on 2009-01-07
Hello.

i just installed my TV Card (ADS Tech MCE-306 InstantTV Deluxe PCI TV Tuner Card) which has a Conexant Chipset (CX23880-19).  I get video just fine, but i can not get any audio.  The card is detected:

```

cat /proc/asound/cards 
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf6bfc000 irq 16
 1 [CX8801         ]: CX88x - Conexant CX8801
                      Conexant CX8801 at 0xf8000000

```

i am running 8.10 with pulse audio.

Any ideas on how to get the sound to work?

thanks,
-=- adam

---

