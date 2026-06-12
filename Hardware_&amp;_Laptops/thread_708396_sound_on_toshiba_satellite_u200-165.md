---
title: "sound on toshiba satellite u200-165"
date: 2008-02-26
forum: Hardware &amp; Laptops
---

### Post by t0bias on 2008-02-26
hi,

my toshiba satellite u200-165 has got a a intel hd-audio-device which seems to be detected but is not working.

lspci gives
```
 [00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```

lspci -nv|grep -A1 0403 gives
```
00:1b.0 0403: 8086:27d8 (rev 02)
        Subsystem: 1179:0001
```


aplay -l gives
```
Intel [HDA Intel], Device 0: AD198x Analog [AD198x Analog]

```


i tryied the following steps to solve the problem:
```
cd /usr/src
sudo module-assistant update
sudo module-assistant prepare
sudo module-assistant auto-install alsa

```

i also tryied the following options in /etc/modprobe.d/alsa-base
(one at a time of course...)
```

options snd-hda-intel model=toshiba
options snd-hda-intel model=basic
options snd-hda-intel model=auto
options snd-hda-intel model=laptop
options snd-hda-intel model=laptop-eapd
options snd-hda-intel model=3stack
options snd-hda-intel model=uniwill-m31
options snd-hda-intel index=0

```
no success.

i also filled in a bug-report, but no answer so far, maybe i get help in this forum...

any help would be greatly appreciated!!

thanks,

toby

---

### Post by mh1272 on 2008-03-17
This procedured worked for my U205-5058.  
Now/Again, I have sound.

I tested only two (2) options settings and both worked.

options snd-hda-intel model=3stack
options snd-hda-intel model=toshiba

Sound worked properly after the initial 7.10 installation.
I don't use sound often so I don't know if an updates hosed the sound system.
The above procedure worked and now the speakers are producing sound.
I don't know about the headphones yet.  When I get home, I will try them.

Thanks again for the procedure!

:popcorn:

---

