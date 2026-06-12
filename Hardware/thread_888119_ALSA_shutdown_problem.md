---
title: "ALSA shutdown problem"
date: 2008-08-12
forum: Hardware
---

### Post by iamajd on 2008-08-12
This problem is more like a minor annoyance.  It has only two symptoms:

Symptom 1)
While "Shutting Down ALSA" as the computer is shutting down, the following appears:
```
alsactl store: get_control: 209: Cannot read control info '2,0,0,Master Playback Volume,0': No such file or directory
```

Symptom 2)
Since "alsactl store" always fails, sound levels are reset at boot (there is an annoying hiss from CD and Mic that goes away when they are muted).

Possible symptom 3)
I think the volume slider sticks to the top in the volume control applet (I'm not on the 'offending' computer currently and I've done a lot of testing, so I'm not entirely sure).

Other info:
The computer in question is a Toshiba Satellite A105-S1014.
I've appended /etc/modprobe.d/alsa-base with "options snd-hda-intel probe_mask=8 model=auto"
Sound works in the LiveCD, but "sudo alsactl store" has the same error.
I believe this to be new as of Hardy Heron.

Please let me know what info/files I might include to be of the utmost assistance.

---

