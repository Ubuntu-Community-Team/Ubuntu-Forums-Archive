---
title: "ESD looking for the wrong sound card"
date: 2007-01-24
forum: Hardware &amp; Laptops
---

### Post by Pablasso on 2007-01-24
i recently changed my sound card from a FM801 to a VIA VT1720/24, before i had esd working fine with any program, but after the change i can't get it to start the service

i already selected Chaintec AV-710 on the Sound preferences as the default card and ticked the checkbox to use the sound server, but its still not working

trying to start it via shell throws me this:

```
pablasso@uterra:~$ esd 
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card 'FM801AU'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM default
```

wich makes sense, since it's looking for the old FM801AU instead of the new one.. how can i make it to look for the appropiate driver? using the -d option is still useless (/dev/dsp is my only card as i disabled the onboard)

```
pablasso@uterra:~$ esd -d /dev/dsp 
- using device /dev/dsp
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM /dev/dsp
```

thanks for your help :)

---

### Post by Pablasso on 2007-01-24
my output from /proc/asound/cards is:

```
pablasso@uterra:~$ cat /proc/asound/cards 
 0 [AV710          ]: ICE1724 - Chaintech AV-710
                      Chaintech AV-710 at 0xdea0, irq 209

```

when i set this on ~.asoundrc

```
pcm.!default {
    type hw
    card 0
}
ctl.!default {
    type hw
    card 0
}

```

and trying to start esd on shell.. it throws me this:

```
pablasso@uterra:~$ esd
Audio device open for 44.1Khz, stereo, 16bit failed
Trying 44.1Khz, 8bit stereo.
Audio device open for 44.1Khz, stereo, 8bit failed
Trying 48Khz, 16bit stereo.
Audio device open for 48Khz, stereo,16bit failed
Trying 22.05Khz, 8bit stereo.
Audio device open for 22.05Khz, stereo, 8bit failed
Trying 44.1Khz, 16bit mono.
Audio device open for 44.1Khz, mono, 8bit failed
Trying 22.05Khz, 8bit mono.
Audio device open for 22.05Khz, mono, 8bit failed
Trying 11.025Khz, 8bit stereo.
Audio device open for 11.025Khz, stereo, 8bit failed
Trying 11.025Khz, 8bit mono.
Audio device open for 11.025Khz, mono, 8bit failed
Trying 8.192Khz, 8bit mono.
Audio device open for 8.192Khz, mono, 8bit failed
Trying 8Khz, 8bit mono.
Sound device inadequate for Esound. Fatal.

```

:confused:

---

### Post by Pablasso on 2007-01-24
i did [this]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_configure_sound_to_work_properly_in_GNOME") and still nothing

```
pablasso@uterra:~$ esd
ALSA lib pcm_direct.c:849:(snd_pcm_direct_initialize_slave) requested or auto-format is not available
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to initialize slave

```

---

