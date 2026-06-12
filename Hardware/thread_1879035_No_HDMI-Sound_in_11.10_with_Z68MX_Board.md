---
title: "No HDMI-Sound in 11.10 with Z68MX Board"
date: 2011-11-10
forum: Hardware
---

### Post by |Shark| on 2011-11-10
Hello Folks

I checked out the search before but I can't find something which suits my problem

I got a new HTPC with a Gigabyte Z68MX-UD2H-B3 and an i5-2300. It's running oneiric on it but when I connect my TV via hdmi to it I cannot get any sound. I tried all modes the sound configuration offers me but even the speaker test doesn't bring anything up.

Does anyone know the problem or a way how I could fix it?

Greetings
|Shark|

EDIT: Solved by Alsa-base.conf

---

### Post by bryanl on 2011-11-11
For HDMI output, there are two places in sound settings that have to be set to HDMI. First is the 'Hardware' tab, which is where the 'test speakers' button is. Second is the 'Output' tab where you need to select both the HDMI output and the connector.

The 'test speakers' button should come up with a box that lets you select the speaker to test. It appears to go directly to the selected sound device rather than the 'Output' tab's selection so, if that doesn't produce output, the first thing to do is to make sure that the volume is turned up on both the sound settings and on the TV.

Sometimes I have had to use the mixer in order to make sure the volumes are set, especially for the input I am trying to use. The test button shouldn't need that, I'd think, but the mixer might be something to play around with as well.

Also check to make sure the mobo supports sound to the HDMI port and if any settings or jumpers are needed to enable this. Since its an HTPC, I'd assume this was all set but when things don't work, all assumptions need verification. -- as a part of this basic checks thing, also connect speakers to the output jack on the mobo and make sure you can get sound there to verify sound is being output somewhere.

---

### Post by |Shark| on 2011-11-12
I just checked the output tab and there is just a "Dummy" device listed. 

Also aplay -l gives:
aplay: device_list:240: no soundcards found...

Any Idea why Ubuntu does this?

---

### Post by |Shark| on 2011-11-25
Heyho

After I updated to new Kernel and added followint line to /etc/modprobe.d/alsa-base.conf it worked suddenly...
```

options snd-hda-intel model=ICH7
```

---

