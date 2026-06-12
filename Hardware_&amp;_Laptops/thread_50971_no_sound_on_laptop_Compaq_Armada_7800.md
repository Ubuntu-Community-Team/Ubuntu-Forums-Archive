---
title: "no sound on laptop Compaq Armada 7800"
date: 2005-07-22
forum: Hardware &amp; Laptops
---

### Post by teodoor on 2005-07-22
type: Compaq Armada 7800 6366/T/14.0/V/0/1

After installing Ubuntu 5.04 I had no sound.
I also had to adjust the xorg.conf file because I could not change the screen resolution: in the monitor section of the file I added two lines:
HorizSync 30-96
VertRefresh 50-80

I tried to restart alsa, no problem
but when I start esd, I get these errors

cursus@ubuntu:~$ sudo /etc/init.d/alsa restart
Password:
 * Shutting down ALSA...                                                 [ ok ]
 * Setting up ALSA...                                                    [ ok ]
cursus@ubuntu:~$ esd
ALSA lib confmisc.c:550:(snd_determine_driver) could not open control for card 0
ALSA lib conf.c:3463:(_snd_config_evaluate) function snd_func_card_driver return ed error: No such file or directory
ALSA lib confmisc.c:387:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3463:(_snd_config_evaluate) function snd_func_concat returned er ror: No such file or directory
ALSA lib confmisc.c:945:(snd_func_refer) error evaluating name
ALSA lib conf.c:3463:(_snd_config_evaluate) function snd_func_refer returned err or: No such file or directory
ALSA lib conf.c:3932:(snd_config_expand) Evaluate error: No such file or directo ry
ALSA lib pcm.c:2068:(snd_pcm_open_noupdate) Unknown PCM default
cursus@ubuntu:~$

---

### Post by s_p_a_r_k_y on 2005-07-22
what if you try to play something directly yo the sound card? I usually test it that way to make sure that alsa is working in the first place. I usually download xine 
```
 sudo apt-get install xine-ui
```
and I believe you can tell that to use the ALSA driver directly instead of using esd. I have mine setup that way, as I prefer not to use esd (I actually kill esd everytime I log in).

Also, can you change volume and such with alsamixer?

---

