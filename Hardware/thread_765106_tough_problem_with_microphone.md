---
title: "tough problem with microphone"
date: 2008-04-24
forum: Hardware
---

### Post by elric83 on 2008-04-24
Hi everyone,
I have just installed ubuntu 8.04 on my laptop (Benq, joybook s53) and all is working fine except the internal and external microphone. It is not a so big problem but I am not able to resolve it in any way!! This problem has been always present on my laptop also in ubuntu 7.
The output of lspci for my audio device is:

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)

I tried to look for a solution around the internet and I found a discussion about it (see [https://bugtrack.alsa-project.org/al...ew.php?id=1134](https://bugtrack.alsa-project.org/al...ew.php?id=1134) ) but I am not able to apply it because I am quite a noob....

Could someone plese help me? thanks!

---

### Post by Ub1476 on 2008-04-24
We'll use the CLI way cause it's faster:

```
alsamixer
```

Now press F4, this is the section for capturing sound.

Turn up the volume (arrow keys) and press <Space> to set one of the devices for capturing.

---

### Post by elric83 on 2008-04-25
I have tried but nothing has changed... I attached the screenshot of alsamixer in the configuration I am using it but I have tried also many other combination (each channel seted to capture). 
Thank you anyway, every help is well accepted. Other ideas?

---

### Post by coreoatetosi on 2010-02-16
Hi,
this problem still exist with this audio card.
I have the same laptop, i've just installed Ubuntu Karmic and I've update the alsa module to the last version; but the microphone doesn't works, and the audio is not perfect.
Have you solved this problem?

---

