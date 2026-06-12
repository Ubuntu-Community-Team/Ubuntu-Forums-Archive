---
title: "No sound with Intel 82801 (Sony Vaio PCG TR2MP)"
date: 2005-05-23
forum: Hardware &amp; Laptops
---

### Post by jannek on 2005-05-23
I have installed Ubuntu 5.04 on my Sony Vaio PCG TR2MP. Unfortunatly sound is not workingat all, No system beebs  no xmms...

/proc/asound/cards: 
```
0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                    Intel 82801DB-ICH4 with AD1981B at 0xe0100c00, irq 9
``` 


lspci | grep -i audio : 
```
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
``` 

ps -e | grep esd 
```
8382 ?        00:00:01 esd
``` 

lsmod

```
... 
snd_intel8x0           29984  2
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixe r_oss,snd_pcm,snd_timer
soundcore               9824  3 snd 
...
``` 

Some ideas how to go on from here???

---

### Post by jannek on 2005-05-24
Sorry, I simply forgot to turn off the External Ampliphier in the "alsamixer" which is turned on after installation...
 
Never mind....

Nice Greetings,

Jannek

---

### Post by javafreak on 2005-06-18
Thanks for posting your reply jannek. I had the same issue.

---

### Post by jacksenechal on 2007-12-19
Indeed, this was the case for me as well. Too bad it is turned on by default... I was avoiding fixing the sound on this laptop for months, as I thought it would be a big ordeal!

Just in case anyone is reading this post and doesn't know how to turn off the "external amplifier", it's easy. Right click on the speaker icon in the top right of the screen, select "Open Volume Control", then click the Edit->Preferences menu Check the "External Amplifier" box. Now back in the volume control window, there's a tab that says "Switches", and a checkbox where you can turn off the external amplifier.

Cheers,
Jack

---

