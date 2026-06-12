---
title: "Asus Xonar D2X no sound?"
date: 2017-04-09
forum: Hardware
---

### Post by deanium on 2017-04-09
Hi,

I've got an install of Ubuntu Gnome 16.04 on my rig- however am getting no sound from my Xonar D2X. I have it working fine in my windows install connected to my AVR via optical, sending 5.1ch (DTS: Interactive). On Ubuntu I have alsa installed and it seems to be detected, however no audio is hitting the AVR.

From what I can find it should be supported by alsa and should pretty much just work- even if I only get 2 channels over optical it'd be a start.

Anyone have any ideas?

Cheers,
Dean

---

### Post by paulisdead on 2017-04-10
I've got the same card and it worked under 16.04 and is working under 17.04 fine, but I'm using the analog outputs.  Are you trying to use straight alsa, or just the default pulse over alsa in ubuntu?  If it's the default pulse, just go into the gnome settings and select sound, you should have the option to change the output to Digital Output (S/PDIF), it's probably just defaulted to the analog outputs.

---

### Post by deanium on 2017-04-16
OK Turns out I'm an idiot- had my amp set to fixed mode DTS- which is fine when I've got the driver running in Windows outputting DTS Interactive, however obviously ignores stereo PCM over optical. That said, anyone know of a way to enable DTS Interactive / Dolby Digital Live features on this card under 16.04? I'm getting stereo over optical now but the reason I bought the card to begin with was to encode 5.1ch over optical using DD:L / DTS:I. I know that the UniXonar project has helped a massive amount on Windows, anything similar for linux?

---

### Post by paulisdead on 2017-04-16
Funny, for the life of me I can't get windows 10 to output more than stereo, but surround works perfectly in Ubuntu, but I'm using analog.

Did you select the right profile from the drop down menu under sound in Gnome Settings?

If that didn't work you could try manually setting it to 5.1 in /etc/pulse/daemon.conf and reboot.
```
default-sample-channels = 6
```

---

