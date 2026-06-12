---
title: "Ubuntu: Acer Aspire TimelineX 3820TG internal microphone not working"
date: 2011-08-16
forum: Hardware
---

### Post by Lapthorb on 2011-08-16
Hi everyone,

I have an issue with my internal microphone and I think with the line-in plug as well.
It is not recording any sound and I do not see any input.

The same thing happens when I connect an external microphone - unfortunately I only have a headset with one plug, so I do not know whether it is not working, because of that...

I found this thread [http://ubuntuforums.org/showthread.php?t=1501525](http://ubuntuforums.org/showthread.php?t=1501525) where there was a sound problem on the same laptop was solved by updating the alsa drivers. But when I run 

```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```

I get almost the same update, but with a newer alsa driver:

```
thorben@Lapthorb:~$ uname -a
Linux Lapthorb 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
thorben@Lapthorb:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC271X Analog [ALC271X Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC271X Digital [ALC271X Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
thorben@Lapthorb:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
thorben@Lapthorb:~$ head -n 1 /proc/asound/card*/codec#*

```

Another difference is the codec: Where it says in the other thread 
```
/proc/asound/card0/codec#0 Codec: Realtek ALC269
/proc/asound/card1/codec#0 Codec: ATI R6xx HDMI 
```

it says in my output:
```
thorben@Lapthorb:~$ head -n 1 /proc/asound/card*/codec#*
```

Can this codec be the issues? Are there other ways to test the microphone?

On the net I only find issues with older Ubuntu Versions - I am already running 64 bit 11.04. 

Thank you very much in advance!

---

### Post by The Geeko on 2011-08-27
I, too, am very much interested in your inquiry.  I have a Gateway NV55S.  I have installed Ubuntu 11.04 [64 bit], also.

So, the machines are different... but my sound card is identified as the same as yours:  ALC271X.

In my case, I have not tested the microphone, yet.  I cannot get sound at all, though.

When i look at the Codecs, this is what I get... which seems to be the opposite of yours... maybe this is my problem?

> 
$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: ATI R6xx HDMI

==> /proc/asound/card1/codec#0 <==
Codec: Realtek ALC271X


and aplay -l reveals
> 
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 0: ALC271X Analog [ALC271X Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


This is where I noticed the difference... card0 and card1 seem to be opposite... I'm not familiar enough with Linux to know if this has any impact on my issue...

I've been investigating my issue for 2 days now... any assistance will be much appreciated.

---

### Post by The Geeko on 2011-08-28
> **Lapthorb said:**
> Hi everyone,

I have an issue with my internal microphone and I think with the line-in plug as well.
It is not recording any sound and I do not see any input.
<snip><snip><snip>
On the net I only find issues with older Ubuntu Versions - I am already running 64 bit 11.04. 

Thank you very much in advance!

Lapthorb,

I got my sound problem fixed by following the procedure at the [Sound Troubleshooting Procedure page]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure").  I suggest that you try this excellent resource as well...

Like your box, mine is 11.04; and our sound cards are the same... so this may just be what you need to resolve your issue.

Good Luck!

---

