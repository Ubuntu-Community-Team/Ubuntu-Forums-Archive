---
title: "Sound problems. Skype and the second session"
date: 2005-11-01
forum: Hardware &amp; Laptops
---

### Post by acehigh on 2005-11-01
Hi all,

I'm new to the forum and I'm not so expert in solving this problem, so I'm asking help to you all.
I have Hoary on an ASROCK K7VT4A PRO ((VIA KT400A chipset). The sound on motherboard works fine (I hear startup/shutdown sounds, gnome sounds, XMMS, Totem, and all) but I wasn't unable since now to solve these problems:
1) I install skype (with synaptic) and when I do the test 'echo123' skype locks up. I have to kill it. (p.s. The mic and phones are ok and activated by alsamixer)
2) When I launch another login session (to login as a different user) the second user doesn't hear any sound: no gnome, no startup sound, nothing.

Any suggestions?

---

### Post by acehigh on 2005-11-04
I'm posting an update to explain that I'm putting these 2 probs together because I think that are both related to the same audio problem.

I did some furhter experiments and:
- The mic and headset are working ok ( I hear the voice from the mic back in the headset/speakers), but I'm not able to record a clip with the gnome sound recorder. If I start to record, the recorder hangs up
- These things happens if I enable the gnome sound server or not.

```
lspci | grep audio
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
```
and
```
 lsmod | grep snd
snd_via82xx            27616  2
snd_ac97_codec         74208  1 snd_via82xx
snd_pcm_oss            52516  1
snd_mixer_oss          19776  1 snd_pcm_oss
snd_pcm                94920  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25156  1 snd_pcm
snd_page_alloc          9796  2 snd_via82xx,snd_pcm
snd_mpu401_uart         7744  1 snd_via82xx
snd_rawmidi            24928  1 snd_mpu401_uart
snd_seq_device          8524  1 snd_rawmidi
snd                    55268  11 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10080  2 snd
gameport                4544  2 snd_via82xx,analog

```

Any suggestion appreciated, thanks

---

