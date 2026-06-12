---
title: "No sound in Ubuntu 8.04 hardy heron"
date: 2008-11-04
forum: Hardware
---

### Post by mtgmutton on 2008-11-04
I'm not sure why, but I have no sound. I'm in Linux Mint Elyssa, which is almost exactly the same as Hardy Heron (but with less issues on my box)... I've tried just about everything with the volume control plugin that goes on the gnome panel, but nothing works. Yes my speakers and sound card are plugged in. :) 

I'm at a loss... :confused:

---

### Post by Bakon Jarser on 2008-11-04
This thread covers just about everything sound related.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by JustTCO on 2008-11-04
Try this post. that save my day in ubuntu 8.04

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by mtgmutton on 2008-11-05
I ran "dmesg" and found snd... it looks like this:

```
[   55.016990] snd-ca0106: Model 1007 Rev 00000000 Serial 10071102
```

But I couldn't figure out what to do with it.... so I moved on.

When I typed in:
```
cat /proc/asound/card0/codec#* | grep Codec
```

I got:
```
cat: /proc/asound/card0/codec#*: No such file or directory
```

So I looked in Thunar, and that file really doesn't exist... For some reason, it's in the "card1" folder... so I used that instead and got this:

```
 cat /proc/asound/card1/codec97#0/ac97#0-0
0-0/0: Analog Devices AD1980

PCI Subsys Vendor: 0x1028
PCI Subsys Device: 0x019d

Capabilities     : -headphone out-
DAC resolution   : 20-bit
ADC resolution   : 16-bit
3D enhancement   : No 3D Stereo Enhancement

Current setup
Mic gain         : +0dB [+0dB]
POP path         : pre 3D
Sim. stereo      : off
3D enhancement   : off
Loudness         : off
Mono output      : MIX
Mic select       : Mic1
ADC/DAC loopback : off
Double rate slots: 10/11
Extended ID      : codec=0 rev=0 AMAP LDAC SDAC CDAC DSA=0 DRA VRA
Extended status  : LDAC SDAC CDAC VRA
PCM front DAC    : 44100Hz
PCM Surr DAC     : 44100Hz
PCM LFE DAC      : 44100Hz
PCM ADC          : 44100Hz



AD18XX configuration
Unchained        : 0x1000,0x0000,0x0000
Chained          : 0x0000,0x0000,0x0000
```

I don't see the "codec" that the site you suggested implies is there... what should i do?

---

### Post by Bakon Jarser on 2008-11-05
Why would you follow his link to a thread that is clearly designed to help people with hda intel sound cards instead of the link that I provided which is written by someone who clearly knows a lot about sound in Ubuntu?  The guide probably failed because you probably don't have an intel sound card.

---

### Post by mtgmutton on 2008-11-05
My apologies, but honestly it only told me his post in the e-mail, and I just followed the link through that... and I actually DO have an intel sound card... it's a dell dimension 3000.

---

### Post by mtgmutton on 2008-11-05
HOORAY I FIXED IT AND ALMOST BLEW MY EARS OUT!!!!

it turns out it was on the wrong device (which was labeled differently than my sound card). but the actual issue was that in the "switches" menu something was checked that apparently shouldn't be...

Thanks much for all your help!

:popcorn:

EDIT: problem being, now I can't get any sound in videos... any ideas on how to fix that?

---

### Post by Bakon Jarser on 2008-11-05
Glad to hear you have made some progress.  If you can't find the answers in the sound guide I posted then maybe there will be an answer in this multimedia guide.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by mtgmutton on 2008-11-06
It didn't work...

---

### Post by glenmo on 2008-11-22
> **mtgmutton said:**
> HOORAY I FIXED IT AND ALMOST BLEW MY EARS OUT!!!!

it turns out it was on the wrong device (which was labeled differently than my sound card). but the actual issue was that in the "switches" menu something was checked that apparently shouldn't be...

Thanks much for all your help!

:popcorn:

EDIT: problem being, now I can't get any sound in videos... any ideas on how to fix that?

it would be really helpful if you explained how you fixed it...

---

### Post by mtgmutton on 2008-11-22
sure

the wrong device was selected. I selected the right device, "CA0106(alsa mixer)". in the switches menu, "IEC958" was checked. I unchecked it and it turned on the sound... a bit louder than expected  :)

---

### Post by glenmo on 2008-11-22
oh... dangit.


tried all the options there and it still didn't help.

i'm on a gateway 4540 with an "Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)" accorging to lspci.

no sound with any of the options... 

i'll be trying the links now... anyone else have any suggestions?  i'm using linux mint 5r1 on this particular machine...

---

### Post by sarthorks on 2008-11-22
mtgmutton.

Go to sound settings (system->preferences->sound in ubuntu)

Play around with the "Music & Movies" sound playback drowdown menu, and hit on Test on every change. I'm pretty sure you'll find your match there.

---

### Post by mtgmutton on 2008-11-22
thanks :) 
I found one under "music and movies" that works when i click "test", but it still doesn't produce sound during video (an avi file). Could it be a codec thing?

---

### Post by sarthorks on 2008-11-22
i have no clue.
try restarting your system.

---

### Post by sarthorks on 2008-11-22
i have no clue.
try restarting your system.

---

### Post by mtgmutton on 2008-11-24
Sorry for the delayed response.

Restarted (twice) but it still doesn't work right... I get sound in games and music, and system sounds still play, but no video... it's really weird

:???:

---

