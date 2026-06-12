---
title: "No Audio In Dapper-Errors W/Alsa Conf?"
date: 2008-05-31
forum: Hardware
---

### Post by theravenproject on 2008-05-31
Okay-I have Gigabytes Brand Spanking New Mobo (Amongst a bunch of other high end stuff that Linux doesn't seem to get along with!) it is the X48T-Dq6 a DDR 3 based high perf Mobo...the onbooard audio is a realtek chip-I believe it is 8 Channel or maybe 7.1 but whatever...I tried Googling the Prob w/no succesful results, and I went through (Must've been fifty) threads here at the Forums w/o anything that I could discern as being pertinent to my particular brand of malady so...it is not working, **I am running Dapper (Becuase Hardy Won't Install w/ my MSI Graphics Card!)** and when I tried:

```
sudo bash
``` (To get Root Privelege) and Then
```
gedit /etc/asound.conf
``` (To Check it out right?  

Here is what I got in Terminal as my response:
```

root@____:~# gedit /etc/asound.conf
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default
```
 
So, can someone help explain what the hell this is /means and how I can go about fixing sound so I can go back to listening to music on this new Mobo (And entire Sys) I paid an arm and a leg to build so that I could game, code, hack, and LISTEN TO MUSIC ON which happens to be my "HAPPY PLACE"-I cnanot hack, code, game or even think without my Chopin!  HELP:confused::confused:

---

### Post by theravenproject on 2008-06-01
*Bump*  HelP?

---

