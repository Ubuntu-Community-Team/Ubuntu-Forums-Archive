---
title: "Frets on fire not liking me"
date: 2008-09-26
forum: General Help
---

### Post by Monotoko on 2008-09-26
Hiya, i tried to install Frets On Fire, the installation went well, after it had installed, i tried to open it, nothing came up, so i tried to open it through the terminal and got:

```
monotoko@danslaptop:~$ fretsonfire
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
Traceback (most recent call last):
  File "./FretsOnFire.py", line 64, in <module>
    engine = GameEngine(config)
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 149, in __init__
    self.audio.open(frequency = frequency, bits = bits, stereo = stereo, bufferSize = bufferSize)
  File "/usr/share/games/fretsonfire/game/Audio.py", line 49, in open
    pygame.mixer.init()
pygame.error: No available audio device

```

Only thing is, it does have an audio device, i know it does, as it plays my music perfectly fine through the speakers and headphones when i plug them in.

can anyone shed any light onto the situation as to why FOF isnt liking my audio?

---

### Post by Monotoko on 2008-09-26
can anyone help me?

---

### Post by schnauzer93 on 2008-09-26
Try doing ```
killall pulseaudio
``` before running it.

---

