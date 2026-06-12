---
title: "Thinkpad SL410 audio jack problem"
date: 2010-01-14
forum: Hardware
---

### Post by tjololo on 2010-01-14
Hi!
Just got my sl410 in the mail and I can't have a laptop without linux so the first thing was to install ubuntu. The sound up/down is working (not the mute button). But the most annoying thing right now is that the audio jack is not working. I got sound and every thing, but if I plug in my headset the sound is still coming from the pc speakers... 
Have anybody fixed this?

---

### Post by IgnasM on 2010-01-14
Hi,

in my case when an audio jack is connected sound is coming both from speakers and headphones. I have to use sound mute button to mute the speaker...

By the way, did you encounter problems described in [this]("http://ubuntuforums.org/showthread.php?t=1356119") topic? And which version of ubuntu are you using?

Ignas M.

---

### Post by tjololo on 2010-01-18
Im running Ubuntu 9.10 x86 (not 64-bit) version.
Have the same problems as in that post. But the other buttons are not a problem, yet. Would have been nice if I could use a headset so I can listen to music while I'm in lectures;)

---

### Post by jfanaian on 2010-01-26
Hi,

Any updates on this? I'm having the same issue on 9.10. Thanks!

---

### Post by tjololo on 2010-03-17
Still not working for me...
Is there any updates regarding this topic? Quite boring at school without music;)

---

### Post by edward_lin on 2010-04-04
I had the same problem on my ThinkPad SL410 (2842-D7V), and successfully solved today.

First, check your chip model:
```
aplay -l
**** PLAYBACK &#30828;&#39636;&#35037;&#32622;&#28165;&#21934; ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```It shows my sound chip is Intel ALC269 (card 0). I guess laptops of other brand with ALC269 may fixed in the same way.

Then, edit /etc/modprobe.d/alsa-base.conf to add few words:
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```add the below line at the bottom of this file:
```
options snd_hda_intel model=lifebook
```Save and reboot. That's all! I know my model is certainly not Lifebook, but the way above really works.

If your chip is not ALC269, the "model" may not be **lifebook**. Maybe you can try any of below. Good luck:

**3stack-dig** 3-jack with SPDIF I/O
**6stack-dig** 6-jack digital with SPDIF I/O
**3stack-6ch** 3-jack 6-channel
**3-jack 6-channel** with SPDIF I/O
**6stack-dig-demo** 6-jack digital for Intel demo board
**acer** Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
**acer-aspire** Acer Aspire 9810
**medion** Medion Laptops
**medion-md2** Medion MD2
**targa-dig** Targa/MSI
**targa-2ch-dig** Targs/MSI with 2-channel
**laptop-eapd** 3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
**lenovo-101e** Lenovo 101E
**lenovo-nb0763** Lenovo NB0763
**lenovo-ms7195-dig** Lenovo MS7195
**haier-w66** Haier W66
**6stack-hp** HP machines with 6stack (Nettle boards)
**3stack-hp** HP machines with 3stack (Lucknow, Samba boards)
**auto** auto-config reading BIOS (default)

---

### Post by tonymoyoy on 2010-04-22
Thanks, it works

---

### Post by mark09baker on 2011-02-01
SORRY--should have looked at the dates before posting.


Adding 

options snd_hda_intel model=lifebook 

to /etc/modprobe.d/alsa-base.conf also works for the the L412, as edward_lin predicted.


aplay -l output:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
     Subdevices: 0/1
     Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
     Subdevices: 1/1
     Subdevice #0: subdevice #0

---

