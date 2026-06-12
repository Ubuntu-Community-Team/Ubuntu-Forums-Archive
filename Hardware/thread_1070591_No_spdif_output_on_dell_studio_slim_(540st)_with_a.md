---
title: "No spdif output on dell studio slim (540st) with alsa 1.0.19"
date: 2009-02-15
forum: Hardware
---

### Post by Sav on 2009-02-15
Hi,
I know this is a known issue, but today I upgraded alsa to the latest 1.0.19 version.
Now I can see the digital output in the "aplay -L" report:

> iec958:CARD=Intel,DEV=0
    HDA Intel, ALC888 Digital
    IEC958 (S/PDIF) Digital Audio Output

I can hear sounds from the analog outputs, but still nothing from the spdif ouput.
I tried to edit the .asoundrc file like this:
> pcm.!default {
        type hw
        card 0
        device 1
       rate 44100
       format s16_le
}

and the /etc/modprobe.d/alsa-base inserting this line:
> options snd-hda-intel probe_mask=1 model=6stack-dell

I also checked the mixer switch with iec958.

Did I miss something?

---

### Post by Sav on 2009-02-24
Solved!

I just installed the latest alsa snapshot.

---

### Post by erlguta on 2009-03-20
Hi Sav. I have this PC too, with the integrated sound card:
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller

The sound card does not work at all (so sound) in intrepid with alsa:
# dpkg -l asla*
ii  alsa-base                                     1.0.17.dfsg-2ubuntu1 

Alsa 1.0.19 is not in the repositories. In Jaunty there is still 1.0.18.dfsg-1ubuntu6

How did you installed alsa 1.0.19 in Intrepid?
Is there any how-to?

I would appreciate your help.
Thank you.

---

### Post by erlguta on 2009-03-20
mmm, i think i have found it:
[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

But my question is:
When i upgrade my Intrepid to Jaunty in April, should i do this process again???...because Jaunty will come with alsa 1.0.18 :( and th installation of the Jaunty kernel wiil overwrite this...isn't it?

---

### Post by erlguta on 2009-03-20
Wow, and the sound works too in Intrepid with the default alsa putting in the /etc/modprobe.d/alsa-base this line:
```

options snd-hda-intel probe_mask=1 model=6stack-dell

```

How should i know that we should put this option?
Where did you find this?
Why in a default Ubuntu installation the sound card simple not works?

---

