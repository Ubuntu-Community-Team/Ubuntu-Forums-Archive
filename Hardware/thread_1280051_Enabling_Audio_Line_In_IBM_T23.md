---
title: "Enabling Audio Line In IBM T23"
date: 2009-10-01
forum: Hardware
---

### Post by tmilliken on 2009-10-01
I have an IBM T23 laptop running xubuntu 9.04. I would like to get the audio line in working. The mic, headphone and line out are working fine. My dock has a line in and a line out connector. I can't seem to figure out if the line in is functional on the laptop with this dock. Line in in the alsa mixer is enabled and the level is up. The alsa mixer is showing the sound card as an Intel 82801CA-ICH3. I believe this is the right chipset. Would I have to edit the config file to get this to work?

Thanks,
Tom

---

### Post by tmilliken on 2009-10-02
Well I did finally figure it out. I needed to add the "line in capture" switch in the alsa mixer.

---

