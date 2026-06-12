---
title: "Asus Laptop VX2 - sound card not working"
date: 2015-11-03
forum: Hardware
---

### Post by shredd2 on 2015-11-03
Hi all,

New to Linux - installed Ubuntu 14.04 LTS on a older legacy laptop I had laying around: Asus Lamborghini VX2.
[COLOR=#000000][FONT=Verdana]Processor (CPU)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Type : Intel® Core™2 Duo Processor T7400[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Speed : 2.166GHz[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]FSB : 667 MHz[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Cache : 4MB L2 cache[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Chipset[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Type : Mobile Intel® 945PM Express Chipset[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Memory[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]RAM : DDRII667MHz, up to 2 GB[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Graphics Card[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]NVidia GeForce Go7700 VX 512MB[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Storage[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]2.5" 9.5mm IDE HDD /w Ultra DMA 100 / S.M.A.R.T. supported[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]160 GB supported[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Connectivity[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Modem : Yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Ethernet : Integrated V.92 MDC Fax/Modem, with AC-Link Version. 2.1 Compliant.and 10/100/1000 Base T [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Wi-fi : Intel® Wireless WiFi Link 4965AGN or Intel® PRO/Wireless 3945ABG Network Connection[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Bluetooth : Built-in Bluetooth™V2.0+EDR (optional feature)[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Audio System[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Built-in High Definition Audio compliant audio chip,[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Built-in speaker and microphone

[/FONT][/COLOR]The audio has been detected as an Intel [HDA Intel], device 0: AD196A Analog

I have tried for days now trying to find information on the internet on how to get this card to work.I have gone through the basics of making sure that nothing was muted, and such. I have tried editing the alsa-base.conf with (options snd-hda-intel model=xxx (I found a large list of Asus models and tried them all), after each sudo edit, I would force the reload on Alsa. Nothing seems to work. If I try to uninstall Alsa and reload (which I saw on one website), it bricks my install and I'm forced to reinstall and do it all over again. I have even gone as far as trying different distro's to see if that worked, and it does not.

Does anyone have any other suggestions?
Kind regards,

---

