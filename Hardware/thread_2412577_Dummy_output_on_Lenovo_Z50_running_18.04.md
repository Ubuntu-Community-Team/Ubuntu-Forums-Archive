---
title: "Dummy output on Lenovo Z50 running 18.04"
date: 2019-02-14
forum: Hardware
---

### Post by ramkashyap117 on 2019-02-14
I can't solve the dummy output problem. Audio stopped working suddenly. Here is the output from some of the commands

```
inxi -A
Audio:     Sound: Advanced Linux Sound Architecture v: k4.15.0-45-generic

aplay -l
aplay: device_list:270: no soundcards found...




```

I tried this ```
 [COLOR=#333333][FONT=&quot]rm -r ~/.config/pulse; pulseaudio -k [/FONT][/COLOR]
```, but didn't work.

```

sudo modprobe snd-hda-intel
modprobe: ERROR: could not insert 'snd_hda_intel': Required key not available

```

Can anyone help me on this

---

