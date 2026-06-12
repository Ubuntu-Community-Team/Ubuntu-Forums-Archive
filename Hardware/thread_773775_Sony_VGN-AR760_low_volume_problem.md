---
title: "Sony VGN-AR760 low volume problem"
date: 2008-04-29
forum: Hardware
---

### Post by Amorget on 2008-04-29
I have been trying to get the volume to actually work at a descent level.  Basically anything below half volume is silent on the internal speakers.

When I run this:
```
cat /proc/asound/card0/codec#* | grep Codec
```

I get:
```
Codec: SigmaTel CXD9872AKD
Codec: Conexant ID 2c06
Codec: Realtek ALC262
```

So, I've been trying by adding this line:

```
options snd-hda-intel model=basic
```

to my alsa-base, I've also tried sony, vaio, auto, and several others.  None seemed to affect the sound.

I've tried installing them gnome-alsamixer and playing with the controls there, but it didn't help.

Does anything have any thoughts that will allow me to run my laptop at a descent volume.

Thanks,
Douglas

---

### Post by Amorget on 2008-05-02
Bump... any ideas for me?

---

### Post by subzero316 on 2008-05-02
er...you cud play your movies in vlc it has volume booster:popcorn:.as for baisc sounds no-idea juschk if you got the right driver installed.

---

### Post by redhound on 2008-05-05
So for my VGN-T2XP/S ... Same problem ...

---

### Post by Amorget on 2008-05-06
Which sound card do you have?  Same one?

---

### Post by redhound on 2008-05-06
Got a solution for my problem ... Would bet that this also fits for your VAIO:

- Enter gnome volume control panel (alsa mixer)
- Enter the "Edit / Settings..." or similar menu (got the German translation ;) )
- Activate the "External Amplifier" track to be visible
- Under the "Switches" tab you now should be able to disable the check on  "External Amplifier"
- Enjoy the sound ..! :grin:


Cheers redhound

---

### Post by Amorget on 2008-05-06
> **redhound said:**
> Got a solution for my problem ... Would bet that this also fits for your VAIO:

- Enter gnome volume control panel (alsa mixer)
- Enter the "Edit / Settings..." or similar menu (got the German translation ;) )
- Activate the "External Amplifier" track to be visible
- Under the "Switches" tab you now should be able to disable the check on  "External Amplifier"
- Enjoy the sound ..! :grin:


Cheers redhound

How exactly are you getting to the gnome volume control panel?  Just by double clicking on the volume icon?  If so, I don't have an "External Amplifer" track.

I have:

Master
Headphone
PCM
Front
Front Mic
Front Mic Boost
Line-In
CD
Microphone
Mic Boost
Mono
Capture
Capture 1
Capture 2
Digital
Input Source
Input Source
Input Source


Thanks!
Douglas

---

### Post by redhound on 2008-05-07
yeah, that's just this mixer application.

what you could try is to activate all tracks and see if you find then an "External Amplifier" checkbox in the Switches tab.

---

### Post by Amorget on 2008-05-07
I enabled all of them, no "Switches" tab appeared...

---

### Post by redhound on 2008-05-07
What's the hardware you've got built in? 

You can find out with

[FONT="Lucida Sans Unicode"] aplay -l
[/FONT]
I added a 

[FONT="Lucida Sans Unicode"] options snd-hda-intel model=IEC958[/FONT]

option in my [FONT="Lucida Sans Unicode"]/etc/modprobe.d/alsa-base[/FONT] as mine has got a Intel 82801DB-ICH4 chipset. To be honest I'm not sure if this was a right setting or changed anything ... But it might worth a try.

Then you've to restart ALSA with

[FONT="Lucida Sans Unicode"] sudo /etc/init.d/alsa-utils restart[/FONT]

Maybe this helps further and you get a bigger set of track controls ??

---

### Post by redhound on 2008-05-07
argh sorry, just have seen that you already tried the alsa-base-trick ...

---

