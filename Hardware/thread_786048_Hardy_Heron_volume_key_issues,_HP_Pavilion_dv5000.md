---
title: "Hardy Heron volume key issues, HP Pavilion dv5000"
date: 2008-05-07
forum: Hardware
---

### Post by mtxcoll on 2008-05-07
Hi, I recently upgraded Ubuntu from Gutsy Gibbon to Hardy Heron on a dv5163cl HP laptop. Sound works fine, but the volume keys no longer function properly; hitting the "volume up" or "volume down" keys sometimes does nothing and sometimes causes only the left-channel or right-channel PCM volume to increase/decrease (or only one of the channels is muted). I have to press the mute key several times to get the volume to actually mute properly. Does anyone else have this problem?:confused:

---

### Post by cshen12 on 2008-05-18
> **mtxcoll said:**
> Hi, I recently upgraded Ubuntu from Gutsy Gibbon to Hardy Heron on a dv5163cl HP laptop. Sound works fine, but the volume keys no longer function properly; hitting the "volume up" or "volume down" keys sometimes does nothing and sometimes causes only the left-channel or right-channel PCM volume to increase/decrease (or only one of the channels is muted). I have to press the mute key several times to get the volume to actually mute properly. Does anyone else have this problem?:confused:
I have a Dell Inspiron 9300 with Nvidia graphics driver.  I have similar issues with the volume control in general and in particular with the buttons.  I can turn the volume all the way down with the volume buttons on my Inspiron, but it seems to change the tone instead.  In other words, I still hear the sound, just not as crisp.  When I turn the volume up using the buttons, I get more treble but a similar volume.  Similarly, when I change the volume using the "Master" option on my Gnome desktop, it also changes the tone and not the volume.  The only way I can change the volume is to adjust the PCM slider.  "Master" does not change the volume.

---

### Post by dysonsphere23 on 2008-07-25
I have a similar problem with Dell Inspiron 9300.  My volume, play/pause, stop buttons were working fine under Gutsy, but since I installed Hardy (clean install) they no longer have any control (the volume buttons cause the display to come up and show the volume bar but the volume does not change).

I think the tone changing is due to the volume of the main speakers changing but the subwoofer not changing (hence the lower tone).  I thought it might be a Pulse Audio problem and messed around with those settings and at one point got that effect.

I then tried implementing this fix:

[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

but the problem persists.

Any ideas/clarification would be much appreciated.

---

