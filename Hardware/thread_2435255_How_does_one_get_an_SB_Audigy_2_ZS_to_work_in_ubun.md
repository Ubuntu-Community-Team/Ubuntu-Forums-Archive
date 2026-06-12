---
title: "How does one get an SB Audigy 2 ZS to work in ubuntu?"
date: 2020-01-18
forum: Hardware
---

### Post by blackburnfjames on 2020-01-18
Hi guys,

Basically, I have an SB Audigy 2 ZS and I was really hoping to get it to work in Ubuntu 19.04!

I know the card is installed because if I run lspci I get:
```

04:06.0 Unassigned class [ffff]: Creative Labs EMU10k2/CA0100/CA0102/CA10200 [Sound Blaster Audigy Series] (rev ff)

```

However because it is an "Unassigned class" I cannot see it under /proc/asound/cards :
```

 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe024000 irq 16
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfcffc000 irq 19

```

I've noticed only those in lspci that have the tag "Audio device" will appear in the list of available audio devices! :o
Yet my card is "Unassigned class", so I was wandering if it simply needs to be forced to be seen as an audio device!

To be completely honest I have never used an SB Audigy 2 ZS before as I have always used an SB Audigy 4, so I could have it plugged into the wrong port :confused:, and when I plug it in to the jack closest to the PCI screw I get a metric ton of static!

Any help would be very much appreciated!

Thanks in advance,
Jim

---

### Post by guiverc on 2020-01-18
I would suggest trying to use Ubuntu 19.10.

Ubuntu 19.04 reaches EOL on Thursday ([https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue613#Ubuntu_19.04_.28Disco_Dingo.29_reaches_End_of_Life_on_January_23_2020](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue613#Ubuntu_19.04_.28Disco_Dingo.29_reaches_End_of_Life_on_January_23_2020)) having already passed 9 months since it was released.  I'd *release-upgrade* first and get it to work on supported release that has more than mere days left.

---

