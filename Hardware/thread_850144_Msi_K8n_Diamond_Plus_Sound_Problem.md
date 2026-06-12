---
title: "Msi K8n Diamond Plus Sound Problem"
date: 2008-07-05
forum: Hardware
---

### Post by fmrfirebird on 2008-07-05
Hello,

I've unable to have sound with the embeded sound chipsed of my motherboard (MSI K8N DIAMOND PLUS). It is an Audigy SE (CA0106) sound chipset. I've run it on my older mandriva 2008, by modifying source code of the CA0106 by adding the serial of my chipset, but when trying the same tips nothing change on Ubuntu 8.04.

The guys of alsa have applyed my patch into their alsa driver .17rc3, and I've retried again, but without success.

Maybee it is a problem in module loading ? or dunno, but if it was possible on mandriva why not on this ubuntu too ?

---

### Post by fmrfirebird on 2008-07-07
Nobody ?

---

### Post by alex-eduardo on 2008-08-20
I have the same problem. 
(MSI K8N Diamond, AMD 64 - Soundblaster Audigy SE, Hardy heron)

Until recently I had a PCI sound-card instead, and when I removed it realized that I've never actually managed to get the on-board sound working with this motherboard.

This guy has a solution for Breezy Badger:
[http://ubuntuforums.org/showthread.php?t=153823]("http://ubuntuforums.org/showthread.php?t=153823")

..but I was hoping I wouldn't have to go through all that without knowing whether it will work with Hardy etc.

Any ideas?

---

### Post by Kevbert on 2008-08-20
Please post the output from terminal of
```
cat /proc/asound/card0/codec#* | grep Codec
aplay -l
```

---

### Post by alex-eduardo on 2008-08-20
In [COLOR="Red"]/proc/asound/card0[/COLOR] I can see:
[FONT="Courier New"][SIZE="2"]
[COLOR="Green"]ca0106_i2c    ca0106_reg8   id      oss_mixer  pcm1c  pcm2p
ca0106_reg16  ca0106_regs1  iec958  pcm0c      pcm1p  pcm3c
ca0106_reg32  ca0106_regs2  midi0   pcm0p      pcm2c  pcm3p[/COLOR][/SIZE][/FONT]

So no 'codec' - am I missing a file?

---

### Post by finito on 2008-08-20
I have this motherboard it worked out of the box for me.

Except for the microphone, did you change some settings?

---

### Post by Kevbert on 2008-08-21
Please take a look at this [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=770497"). Post #7 looks promising.  System-Sound-Devices...

---

### Post by alex-eduardo on 2008-08-24
Thanks Kevbert: I tried the steps in post #7 - but still no sound

I am pretty sure I have tried all the possible combinations in the 'device' dropdowns in
[COLOR="Navy"]'System => Preferences => Sound'[/COLOR] and [COLOR="Navy"]'Preferences => Multimedia Systems Selector'[/COLOR]


Finito: As far as I can tell I have not changed any relevant settings. I've even reinstalled Ubuntu to try with refreshed default sound settings. I will try out a mic when (if) I get sound working.


Any other ideas would be greatly appreciated.

---

