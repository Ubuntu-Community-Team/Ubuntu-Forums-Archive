---
title: "MIDI playback not working on Audigy 2"
date: 2019-03-28
forum: Hardware
---

### Post by user722 on 2019-03-28
I followed this guide.
[https://help.ubuntu.com/community/Midi/HardwareSynthesisSetup](https://help.ubuntu.com/community/Midi/HardwareSynthesisSetup)

[B][FONT=courier new]> aplaymidi -l
 Port    Client name                      Port name
 14:0    Midi Through                     Midi Through Port-0
 16:0    SB Audigy 2 [SB0240]             Audigy MPU-401 (UART)
 16:32   SB Audigy 2 [SB0240]             Audigy MPU-401 #2
 17:0    Emu10k1 WaveTable                Emu10k1 Port 0
 17:1    Emu10k1 WaveTable                Emu10k1 Port 1
 17:2    Emu10k1 WaveTable                Emu10k1 Port 2
 17:3    Emu10k1 WaveTable                Emu10k1 Port 3

> asfxload Unison.sf2
> aplaymidi -p 17:0 000AcPiano.mid[/FONT][/B]

No error messages and aplaymidi exits at appropriate time but also no sound.

All volumes at maximum in GNOME ALSA mixer. Rosegarden sees MIDI events through the Audigy 2 game port from external MIDI controller. Everything seems to work normally except there is no sound. In the Settings window the card profile is Analog Stereo Output.

Ubuntu 18.04 LTS with latest updates.

---

