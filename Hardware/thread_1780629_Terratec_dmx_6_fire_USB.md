---
title: "Terratec dmx 6 fire USB"
date: 2011-06-12
forum: Hardware
---

### Post by Lyric Suite on 2011-06-12
Anyway to get this card to work? I tried to install alsa tools and run envy24control, but nothing happens when i load it from the menu, and when i type it in the terminal it tells me there is no ice1712 device. I googled around a bit and it seems the envy24control works with the PCI version of the card but not with the USB (just my luck i guess). The card shows up under lsusb but that's about it. Should i just give up or is there a way to install this card under Linux, and if not, could anybody recommend a USB audiocard for pro-audio recording that actually DOES work under Linux?

All help is appreciated.

---

### Post by Lyric Suite on 2011-06-12
Nobody can help me with this?

---

### Post by Yellow Pasque on 2011-06-12
Support was added in driver version 1.0.24: [http://www.alsa-project.org/main/index.php/Changes_v1.0.23_v1.0.24#USB_TerraTec_DMX_6Fire](http://www.alsa-project.org/main/index.php/Changes_v1.0.23_v1.0.24#USB_TerraTec_DMX_6Fire)
Use the ALSA Upgrade script to build a 1.0.24 kernel module: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

---

### Post by Lyric Suite on 2011-06-13
Tried it. Alsa upgraded fine but the card wont show using aplay -l. Is there anything else i can do at this point?

---

### Post by Yellow Pasque on 2011-06-13
> Is there anything else i can do at this point?
Well, I can take a look at your info if you run the alsa-info script, but I have a gut feeling you'll have to swim further upstream and communicate with the alsa devs on their mailing list to get it working.
[http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973](http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973)

---

