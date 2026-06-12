---
title: "ALSA &amp; ESS sound card problems"
date: 2005-04-15
forum: Hardware &amp; Laptops
---

### Post by feloc on 2005-04-15
I have installed hoary as a server, everything works fine except I'm having problems while trying to play mp3's.

dmesg gives this:
isapnp: Scanning for PnP cards...
isapnp: Card 'ESS ES1869 Plug and Play AudioDrive'
isapnp: 1 Plug & Play card detected total

When I try to play mp3 file I get this:

ALSA lib confmisc.c:550:(snd_determine_driver) could not open control for card 0
ALSA lib conf.c:3463:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:387:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3463:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:945:(snd_func_refer) error evaluating name
ALSA lib conf.c:3463:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3932:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2068:(snd_pcm_open_noupdate) Unknown PCM default
No default libao driver available.

I have installed isapnptools package, but it didn't help. Am I missing something?

---

### Post by feloc on 2005-04-16
Anyone?

---

