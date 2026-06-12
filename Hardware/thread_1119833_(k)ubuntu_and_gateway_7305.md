---
title: "(k)ubuntu and gateway 7305"
date: 2009-04-08
forum: Hardware
---

### Post by supremedalek on 2009-04-08
Has anyone installed ubuntu (any variant) in a Gateway 7305 laptop successfully? The two main issues I am having is with its sound (lack of) and wireless (not see anybody).

For the sound, it acts like sound is working (does put out the speaker icon on the screen) but nothing is coming out of the speakers. Looking online and using dmesg, it seems I have and intel 82801DB-ICH4 chipset. I ran the sound card lookup script thing from alsa-project.org and got this:

[http://www.alsa-project.org/db/?f=a528f00cdddaa62b89767ebaaacd808d87daef3c](http://www.alsa-project.org/db/?f=a528f00cdddaa62b89767ebaaacd808d87daef3c)

which indicates I need to use the intel8x0 module. But, according to its website [http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0](http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0), it does not cover the 82801DB chip. So, I tried the procedures suggested in [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449), including compiling the module from scratch, but nothing happened. It still seems to report it sees the chip but no sound comes out.

For the wireless, I am experiencing the same. I have tried two broadcom and one Athros minipci cards and in both cases I am told the cards are there and seen (ifconfig, iwconfig) but they cannot see the 46 wireless networks around me (I used iwlist, wifi-radar, and the network manager). I know for sure one of the broadcoms and the Atheros work fine in my other laptop and under ubuntu, so I do not think I can blame them. 

What else should I test? I can provide output for the above commands as needed.

---

