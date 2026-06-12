---
title: "No audio on XXODD 8227D (realtek/intel)"
date: 2009-10-09
forum: Hardware
---

### Post by blackshadeV on 2009-10-09
Hello,

I have a XXODD 8227D and Ubuntu recognized the most of the hardware, and so i taught he know the audio chip to. But  he didn't, i don;t have audio. Can somebody help me with this problem.

(On my windows side of the notebook it works fine.)

Its an realtek/intel  HD audio chip. but more then that i can't find in windows or on the internet.

Someone know how to fix this? A driver or something?

Thanks,
Blackshade

---

### Post by ajgreeny on 2009-10-09
There may be more clues from running ```
lshw -C multimedia
``` in terminal, which will tell you what the system thinks the card is and which driver is being used.  Ignore the bit about superuser, it does not matter for this part of the output.

---

### Post by blackshadeV on 2009-10-10
```
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
```

Okey so he thinks its a Intel sound chip. Well for a part that is true, only its a realtek sound chip too. So how can I fix this? Are there any drivers available?

---

### Post by ajgreeny on 2009-10-10
Don't worry about the realtek bit, it will not matter at all, it's the intel info that was needed, and it does appear to have been a bit of a difficult one in previous ubuntu versions.  Are you using jaunty, as that seems to be better at having usable drivers for the card, so it may be worth trying a live CD of that if you are not already running it.

What does ```
aplay -l
``` give you?

---

### Post by blackshadeV on 2009-10-10
(i am dutch so i hope you can read it)
```
**** Lijst van PLAYBACK hardware-apparaten ****
kaart 0: Intel [HDA Intel], apparaat 0: ALC883 Analog [ALC883 Analog]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
kaart 0: Intel [HDA Intel], apparaat 1: ALC268 Digital [ALC268 Digital]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
kaart 0: Intel [HDA Intel], apparaat 5: ALC268 Analog [ALC268 Analog]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
```I am running on Ubuntu 9.04 (jaunty).
But what do you mean by live cd? the cd from ubuntu 9.04 or the driver cd from my notebook?

---

### Post by ajgreeny on 2009-10-10
You are running 9.04, so forget my query about live CD, it will not help.
Also, sorry, but I can't really help any more either, other than suggestion you use ```
alsamixer
``` in terminal and make sure nothing is set too low or is muted.

---

### Post by blackshadeV on 2009-10-12
if I type alsamixer in my terminal i get:
```
ALSA lib simple_none.c:1536:(simple_add1) helem (MIXER,'Headphone Playback Switch',0,2,0) appears twice or more

alsamixer: function snd_mixer_load failed: Invalid argument

```

So what does that means?

---

### Post by Pengwyn44 on 2009-10-12
Have you tried clicking on the loudspeaker symbol at the top of the screen on the right hand side?
If there is a mark in the box labelled "Mute" that is your problem. I have been caught out that way. Just click to remove the mark.

---

### Post by blackshadeV on 2009-10-13
> **Pengwyn44 said:**
> Have you tried clicking on the loudspeaker symbol at the top of the screen on the right hand side?
If there is a mark in the box labelled "Mute" that is your problem. I have been caught out that way. Just click to remove the mark.

Sorry to say this but.. It isn't muted. So someone an other idea?

---

### Post by Pengwyn44 on 2009-10-14
Hve you tried SYSTEM --> PREFERENCES --> SOUND?
A window opens in which you can test the sounds using alternative drivers.

---

### Post by blackshadeV on 2009-11-01
> **Pengwyn44 said:**
> Hve you tried SYSTEM --> PREFERENCES --> SOUND?
A window opens in which you can test the sounds using alternative drivers.

Well i tried it now. But I have tried all the options (in al the slect lists) but it doesn't change anything. Anyone else an other idea how to solve this

thanks,
Blackshade

---

### Post by blackshadeV on 2009-11-04
The problem is solved by upgrading to 9.10
thanks

---

