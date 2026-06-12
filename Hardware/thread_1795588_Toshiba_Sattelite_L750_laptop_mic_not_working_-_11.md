---
title: "Toshiba Sattelite L750 laptop mic not working - 11.04 64-bit"
date: 2011-07-02
forum: Hardware
---

### Post by Sebastian-Li on 2011-07-02
Hi
  my dad just bought me a new laptop - a Toshiba Satellite L750 Core i5. It runs Ubuntu amazingly fast and looks really cool but my friends cant hear me on skype :( 

If i click on the sound icon, in preferences under Input, I have 'Internal Audio Analog Stereo'. I made sure its unmuted and tried to max the slider but it still doesn't work. 

All other sounds are fine, just not the internal mic. I don't really know what else to try now and booting into Windows just to skype is really annoying me!  

Before posting I did see some other threads on modifying gconf but none of what I read helped me. I'd love to get this working right and would really appreciate some help. Thanks!

---

### Post by tmowad on 2011-07-03
Out of curiosity, do your earphone jacks work?  I have a Toshiba Satellite L755 and can't get the earphones working.  Speakers play and stuff but when I plug in earphones, the speakers keep playing (and no earphone output).  

Just installed skype and looks like my built-in mic doesn't work either.

---

### Post by Sebastian-Li on 2011-07-03
exactly the same for me too

nothing I did within 'Sound Preferences' made any difference either. 

now I see the point in having a 'Laptop Compatibility List' as a sticky with Ubuntu :)

---

### Post by Sebastian-Li on 2011-07-05
Here is some more information if this helps


uname -a 
```
Linux sebastian-laptop 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```cat /proc/asound/version
```
Advanced Linux Sound Architecture Driver Version 1.0.23.
```head -n 1 /proc/asound/card*/codec#*
```
==> /proc/asound/card0/codec#0 <==
Codec: Conexant CX20585

==> /proc/asound/card1/codec#0 <==
Codec: Nvidia GPU 14 HDMI/DP

==> /proc/asound/card1/codec#1 <==
Codec: Nvidia GPU 14 HDMI/DP

==> /proc/asound/card1/codec#2 <==
Codec: Nvidia GPU 14 HDMI/DP

==> /proc/asound/card1/codec#3 <==
Codec: Nvidia GPU 14 HDMI/DP
```

---

### Post by goldshirt9 on 2011-07-05
try setting your 
sound - hardware -to duplex
then test your mic

---

### Post by Sebastian-Li on 2011-07-05
thanks. i did see a comment somewhere else about this and checked already that its in duplex mode (1 analog input/1 analog output). 

i had a look in alsamixer too. for sound input i have:

Mic B
Mic C
Mic E
Mic F
Capture
Analog Mic

Mics B-F can be enabled, but only one at a time. and i never see a volume level indicator

Capture is currently enabled and shows a normal level and is not muted, but this obviously is not my integrated mic. 

Analog Mic cannot be enabled. Maybe this is the one i am supposed to have working?

---

### Post by lidex on 2011-07-06
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=thinkpad" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by Sebastian-Li on 2011-07-08
wow it worked!!! awesome thanks so much!! 

what did that command actually do btw? i noticed too that the input options in alsamixer have changed...now there is only 'capture' and 'analog mic boost'. 

:D

---

### Post by lidex on 2011-07-08
> **Sebastian-Li said:**
> wow it worked!!! awesome thanks so much!! 

what did that command actually do btw? i noticed too that the input options in alsamixer have changed...now there is only 'capture' and 'analog mic boost'. 

:D
Alsa tries to guess the pin configuration of your codec chip. Manufacturers use various permutations to fit their needs. This just tells alsa to use a configuration specific to your model.

---

