---
title: "Microphone's sound is faint on recording"
date: 2009-11-07
forum: Hardware
---

### Post by LuK_green on 2009-11-07
I've got an ASUS F3Ke laptop. I had experienced problem with it's Intel HDA sound chip (Realtek ALC660-VD) which was that plugging headphones didn't switch the laptop speakers off - they were playing simultaneously. I solved the issue by adding "options snd-hda-intel model=lenovo" line to /ect/modprobe.d/alsa-base.conf file. And that is the only option for me that worked, so looking over other models to add in alsa-base won't help, I suppose. But now I have another problem: computer can't record sound from a microphone. I have two microphones in alsamixer: Front Mic and Mic. Front Mic is a built in mic and Mic is an external mic plugged in via mic input. Both mics are working as they are unmuted in alsamixer, but there are two troubles:

1. The sound I can hear in my headphones while I'm speaking to a mic is very loud and clear and the recorded sound of that speaking is very faint. In spite of all mics volume and boost controls in alsamixer are at treir top levels.
2. It's great that I can hear a signal from my mic in my headphones - good for testing purposes (see point 1), but I'd like to switch it off though. To have a normal voice communication over internet, for example =)

Please, help me with these problems!

---

