---
title: "Sound playing through speaker and headphones"
date: 2016-04-22
forum: Hardware
---

### Post by RockJake28 on 2016-04-22
[COLOR=#111111][FONT=Ubuntu]I have an Asus ROG G752VY dual booted with win 10 and Ubuntu 15.10
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Everything works fine in windows. Switching to Ubuntu the speakers work fine but as soon as I plug in the headphones nothing worked.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I added the following line to [/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]to /etc/modprobe.d/alsa-base.conf

[/FONT][/COLOR]```
[COLOR=#111111][FONT=Ubuntu]options snd-hda-intel model=asus-mode5[/FONT][/COLOR]
```[COLOR=#111111][FONT=Ubuntu]

(I tried asus-mode1 through to 8 too)[/FONT][/COLOR]

[COLOR=#111111][FONT=Ubuntu]the headphones now work beautifully, but sound is still played through the speakers.
[/FONT][/COLOR]
Here are some outputs I have:

```

$ lspci | grep -i audio
00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
01:00.1 Audio device: NVIDIA Corporation GM204 High Definition Audio Controller (rev a1)

```

[COLOR=#111111][FONT=Ubuntu]Auto-mute is enabled in alsamixer[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]After looking in pavucontrol even though the headphones are plugged in, it thinks they are not plugged in. It appears to be treating the headphones as an extension of the speaker as when I change the "speaker" volume in alsamixer it changes the volume through the headphones too.
I have also upgrade alsamixer to the latest version which hasn't helped anything.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Also, the built-in microphone isn't working, though it works fine in Windows.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Any ideas?[/FONT][/COLOR]

---

### Post by Yellow Pasque on 2016-04-22
Is your headphone jack strictly a headphone jack or is it a headset/combo jack? I looked at some screenshots of your laptop, but none were detailed enough for me to see the icons next to the audio jacks.

If it's a combo jack, I think I would try removing model=asus-modeX line and using hda-jack-retask:
```
sudo apt-get install alsa-tools-gui
hdajackretask   #may need sudo, can't remember
```

If it's not too much trouble, get more info
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by RockJake28 on 2016-04-25
Brilliant, I managed to get it working using this.

However, I've now lost volume control. If I open alsamixer, I can adjust the master volume which works perfectly, but the volume control in the top right doesn't work at all

EDIT: A reboot fixed this issue!

---

### Post by Yellow Pasque on 2016-04-25
Great! Please mark the thread solved (thread tools menu above the first post).

---

