---
title: "No sound from internal speakers (Ubuntu 20.04, HP Pavillion ce3520na)"
date: 2020-06-28
forum: Hardware
---

### Post by mishamtrop on 2020-06-28
The internal speakers in my laptop do not work. They are recognised by the system but they produce no sound. Headphones work normally.

I've actually found a solution that worked perfectly for a while (blacklisting [COLOR=#000000]*snd_hda_codec_realtek, *[/COLOR][https://ubuntuforums.org/showthread.php?t=2443366](https://ubuntuforums.org/showthread.php?t=2443366)), but it recently went back to silence, perhaps after a system update.

I've tried reinstalling alsa and pulseaudio and checking alsamixer but to no avail.

---

