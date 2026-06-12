---
title: "Audigy Rx: no MIDI"
date: 2021-04-19
forum: Hardware
---

### Post by diederick2 on 2021-04-19
I own a  Soundblaster Audigy Rx and installed Ubuntu Studio on my PC. Following the instructions on [https://help.ubuntu.com/community/Midi/HardwareSynthesisSetup?action=show&redirect=MidiHardwareSynthesisSetup](https://help.ubuntu.com/community/Midi/HardwareSynthesisSetup?action=show&redirect=MidiHardwareSynthesisSetup). I did
```

$ [FONT=monospace][COLOR=#005fd7]aplaymidi[/COLOR][COLOR=#00afff]-l[/COLOR]
 Port    Client name                      Port name 
 14:0    Midi Through                     Midi Through Port-0 
 16:0    SB Audigy 5/Rx [SB1550]          Audigy MPU-401 (UART) 
 16:32   SB Audigy 5/Rx [SB1550]          Audigy MPU-401 #2 
 17:0    Emu10k1 WaveTable                Emu10k1 Port 0 
 17:1    Emu10k1 WaveTable                Emu10k1 Port 1 
 17:2    Emu10k1 WaveTable                Emu10k1 Port 2 
 17:3    Emu10k1 WaveTable                Emu10k1 Port 3
[/FONT]
```

which, if I understand it correctly, means that my card has an internal MIDI synthesizer. After loading a sound font however, I still don't hear any sound when using aplaymidi to play one of the MIDI files that came with the card:

```

[FONT=monospace][COLOR=#005fd7]$ asfxload[/COLOR][COLOR=#00afff]/usr/share/sounds/sf2/default-GM.sf2[/COLOR]
$[/FONT][FONT=monospace][COLOR=#005fd7] aplaymidi[/COLOR][COLOR=#00afff]-p[/COLOR][COLOR=#00afff]17:0[/COLOR][COLOR=#00afff]NOCTURNE.mid[/COLOR][/FONT]

```

Did anyone successfully use the hardware synthesizer on this card for MIDI, and if so, how?

Thanks for any help.

---

