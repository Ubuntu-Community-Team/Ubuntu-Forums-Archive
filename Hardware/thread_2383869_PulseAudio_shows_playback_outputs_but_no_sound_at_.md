---
title: "PulseAudio shows playback outputs but no sound at system settings - Ubuntu 16.04"
date: 2018-01-30
forum: Hardware
---

### Post by aidin.hsz on 2018-01-30
I've got a system with two sound cards:
```

$ aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC1150 Analog [ALC1150 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC1150 Digital [ALC1150 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: HiFi [SupremeFX Hi-Fi], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

I was trying to switch to SupremeFX Hi-Fi USB Audio, when I messed up with the built-in audio card. Now, there is no sound on the system.

I went through the Pulse Audio Control:

[ATTACH=CONFIG]278386[/ATTACH][ATTACH=CONFIG]278387[/ATTACH][ATTACH=CONFIG]278388[/ATTACH]

 and system audio settings:

[ATTACH=CONFIG]278385[/ATTACH]

, found the palyback devices output but no sound being received in sys. sound settings. It's never been happened to me that setting up a simple audio card is this much tricky. 

Begging for any help/thoughs on this?

---

### Post by tinylagarto on 2018-01-30
What happens if you open

```
alsamixer
```

from the terminal?

Do you see anything muted or otherwise strange?

---

### Post by Yellow Pasque on 2018-01-30
You have the onboard sound card set for digital output (S/PDIF). Is this what you're using?

---

### Post by aidin.hsz on 2018-01-30
I did check alsamixer but not quite familiar. I switched every output to '00' and increased all the volumes, then saved the settings by:

```

sudo alsactl store

```

@[**[COLOR=#000000]Temüjin[/COLOR]**]("https://ubuntuforums.org/member.php?u=327594"), for sure, I'm not using S/PDIF, and tried to change to 'Analogue Stereo Output', but not successful. After any configuration, the ports returned to Digital Output S/PDIF.

---

