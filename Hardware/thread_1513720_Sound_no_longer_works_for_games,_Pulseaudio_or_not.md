---
title: "Sound no longer works for games, Pulseaudio or not"
date: 2010-06-19
forum: Hardware
---

### Post by Dthdealer on 2010-06-19
Yesterday my sound stopped working in games such as Blood Frontier, Tremulous and Assault Cube.  I thought the culprit may have been pulseaudio, so I removed it via apt.
```
  apt-get remove pulseaudio
killall pulseaudio
```

This allowed assaultcube to have sound, but the problem still existed with other games.

My setup is an amp connected to my headphone jack on the laptop ( ACER ASPIRE 5536 ).  The fact some games have sound while others do not shows this is not at fault.

Ubuntu Lucid 64 bit.  "HDA ATI SB".  All output channels are max and not muted in alsamixer.

---

### Post by Dthdealer on 2010-06-19
*solved*
```
 sudo apt-get install libsdl1.2debian-alsa 
```

---

