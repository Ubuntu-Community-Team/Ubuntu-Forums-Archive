---
title: "Bluetooth headset pairs, but no sound/audio"
date: 2015-11-24
forum: Hardware
---

### Post by b00n on 2015-11-24
A friend gave me a Samsung SBH-500 headset.  Browsing online suggests it is from 2008 or 2009.

When I
[LIST]
[*]pair with a telephone, they work great; 
[*]pair with my Ubuntu box they don't work, as described below; 
[*]pair some other headset with my Ubuntu box, the other headset works great. 
[/LIST]

Symptom: pairing appears to go fine -- they show up in [FONT=courier new]System Settings > Bluetooth[/FONT] and I get some fleeble sounds in the headset as they pair.  The also show up in [FONT=courier new]System Settings > Sound[/FONT], but [FONT=courier new][Test Sound] [/FONT]does not play a sound, nor do I get audio if I play something.

One thing that seems odd/suspicious is when I pair other Bluetooth Headsets, I get a drop-down in [FONT=courier new]Settings > Sound > $DEVICE [/FONT]that lets me choose between telephony and A2DP/stereo.  Not with the SBH-500 -- the panel lists balance/fade/subwoofer sliders like [FONT=courier new]Settings > Sound > Headset[/FONT], but nothing like the other Bluetooth devices.

Other hardware includes: Intel NUC running Ubuntu 14.04 and an AirCable Bluetooth adapter via USB.  WiFi is disabled for this computer, but there is other WiFi in the area.

I don't know how to proceed.  I browsed around on Ubuntu forums and on the inter-tuber a bit to try and find somebody else with the same problem or some diagnostics, but found nothing that obviously solved the problems.  Following one thread, I ran [FONT=courier new]pactl list short[/FONT] then turned off the headset and ran it again.  The diff:

```
5d4
< 36    module-bluetooth-device    address="00:02:78:DE:1C:37" path="/org/bluez/8515/hci0/dev_00_02_78_DE_1C_37"    
13d11
< 13    bluez_card.00_02_78_DE_1C_37    module-bluetooth-device.c
```

Any suggestions what else I can try?  Thanks.

---

