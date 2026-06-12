---
title: "Trust Webcam live WB-1300N"
date: 2009-05-27
forum: Hardware
---

### Post by imattacus on 2009-05-27
[SIZE=4]Hi
First off let me just say i'm sorry If this is in the wrong section but its about webcams and a webcam is hardware... plus I use a laptop :D

I have a Tr[/SIZE][SIZE=4]ust webcam live [/SIZE][FONT=arial,sans-serif][SIZE=-1][SIZE=4]WB-1300N and I would like to use it on my ubuntu laptop. First off I plugged it into the laptop to see if it was like already installed and the green light on the webcam went on. I then openend cheese photo booth and it was unable to use my webcam[/SIZE]:o [SIZE=4]So I didnt panic I just went onto the trust drivers site for my webcam. Then I panicked :L I can only download windows drivers!!! I hear you cant use wine so I'm not gonna even try that. I then followed a guide for "easycam 2" and I couldnt make head or tail of it.. I went into the applications sources bit and added in the repository and closed it and refreshed but i got an error about a pubkey refusing to install everything. So i cant even use easycam so I dont know if that works!!! Does anyone know how to either:
Tell me how to work easycam in ubuntu 9.04 (Jaunty Jackolope)
-OR-
Know any other way to install my webcam using either some linux special drivers lol

Sorry if this question has been asked before I cant seem to find any solution to my specific webcam?!?
Anyways, hope you can help :D
[/SIZE][/SIZE][/FONT]

---

### Post by loell on 2009-05-27
can you post the output of ```
lsusb
```

---

### Post by imattacus on 2009-05-29
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 145f:013a  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
I dont see any mention of webcam and my webcam is plugged in

---

### Post by loell on 2009-05-29
the part where it says, **Bus 002 Device 002: ID [COLOR="Red"]145f:013a[/COLOR] ** is your trust webcam, searching it, seems to have a linux driver already.

can you also provide the output of **lsmod** while the webcam is plugged?

---

### Post by imattacus on 2009-06-01
SOrry for the long response. Heres the output of lsmod
```
Module                  Size  Used by
i915                   65540  2 
drm                    96296  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
vboxnetflt             93992  0 
vboxdrv               123048  1 vboxnetflt
input_polldev          11912  0 
sbp2                   30476  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
joydev                 18368  0 
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
ricoh_mmc              11904  0 
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                 10496  0 
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
psmouse                61972  0 
video                  25360  0 
output                 11008  1 video
dcdbas                 15264  0 
serio_raw              13316  0 
ndiswrapper           193436  0 
ohci1394               38576  0 
ieee1394               94660  2 sbp2,ohci1394
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```

---

### Post by imattacus on 2009-06-03
bump.

Anyone know how to help meee!!

---

### Post by imattacus on 2009-06-04
bump.
Anyone know how to fix thiis??? I really need my webcam working and I still havent figured it out

---

### Post by imattacus on 2009-06-06
Bump. Still havent fixed this webcam problem as I dont really know what to do :( anyone know???? please help mee :L

---

### Post by lilie on 2009-11-02
Hello,

I have the same problem with the same webcam (TRUST WB-1300N WEBCAM LIVE), and no solution is available on the Net.

Can anyone help us ?

Thanks

---

### Post by Outtatime on 2011-05-12
Hello All, I'm using Natty (11.04) and got my WB-1300N camera to work with Cheesebooth. What I really wanted to do is use it with Skype, no luck so far on that front. I think I've trawled everywhere for an answer. If I find anything I'll post it.

---

