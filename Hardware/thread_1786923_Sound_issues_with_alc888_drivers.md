---
title: "Sound issues with alc888 drivers"
date: 2011-06-20
forum: Hardware
---

### Post by LemonyZ on 2011-06-20
hello,

I've recently installed xubuntu on my Msi gt740 laptop. Everything has worked so far with the exception of a sound issue.

Currently the system has detected that their is 2 sound devices one for the hmdi and another for the intel hda sound cards which is a realtek alc888. The machine is set up with four speakers and one subwoofer. Currently all sound comes from the sub.

What I've done so far is....

1. Find the model of sound card 

cat /proc/asound/card0/codec* | grep Codec
Which provided: Codec: Realtek ALC888 Codec: LSI ID 1040 

2.Then checked the ALSA documentation for the ALC888

3. Then added the line:
options snd-hda-intel model="MODEL"Into the alsa-base.conf. "Model" being changed for one in the list.

4. Then reset ALSA.
 
I've repeated the process with each model reference with no joy. Am I doing something wrong? 
If I install the realtex unix drivers, I lose the sound completely  and the system will not recognise the device at all. 

Thanks in advance to anyone who can help. :P
LemonyZ

---

### Post by Toz on 2011-06-20
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/796617]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/796617") is a bug report for a similar problem with an MSI GX740. The solution appears to be: ```
options snd-hda-intel index=0 model=acer-aspire-7730g
```

Can you give it a try?

---

### Post by LemonyZ on 2011-06-22
Toz, I almost fell over in disbelief when it worked. Thank you SOOOOO much

LemonyZ:P

---

### Post by Yellow Pasque on 2011-06-22
Please mark thread solved.

---

