---
title: "Headset blocked audio"
date: 2006-10-08
forum: Hardware &amp; Laptops
---

### Post by robcarr2 on 2006-10-08
Hello,

Well I plugged in my USB headset (which I haven't used in ubuntu before), ubuntu recognised it as a sound device, however now I get no sound when I login to Ubuntu, nor do I get sound from any applications apart from VLC, it is the only one which will allow sound, if I log off of ubuntu though I get the log off sound.

Has anyone any ideas?

Thanks, Rob

---

### Post by robcarr2 on 2006-10-10
*bump*

I just typed gnome-volume-control into the terminal and got this:

ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card 'Headset'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default

It seems to be because it cant find the headset (I think)

Please if someone could help it would be appreciated as its driving me crazayyy

**Edit:** I just plugged in my headset and sound was coming through it fine, I then changed default device back to HDA and then sound is coming out of my speakers fine, I dont want to do this everytime though, is there a way of getting rid of any trace of the headset?

---

### Post by GoodPanos on 2006-10-10
Yeah, I ran into the same problem too.

You just have to remember each time you're going to unplug your headsets or shutdown to change the sound driver back to your default which is a simple step; System->Preferences->Sound.

---

### Post by robcarr2 on 2006-10-10
Ah right, simple as that :) Thanks

---

