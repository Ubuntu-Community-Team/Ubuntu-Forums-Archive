---
title: "No Sound on a Gateway 3018GZ"
date: 2010-01-22
forum: Hardware
---

### Post by MasterNetra on 2010-01-22
I recently installed Mint Linux 8 on a relatives old computer. A Gateway 3018GZ Notebook and all seems to be fine except there is no Sound. It uses a "PC2001 Compliant AC '97 Audio" ALSA and OSS drivers don't seem to work. Any ideas?

---

### Post by k64 on 2010-01-23
You could try installing the Windows drivers under Wine. Not saying it's perfect, but worth a shot.

Another idea: Have you tried enabling PulseAudio?

---

### Post by MasterNetra on 2010-01-23
> **k64 said:**
> You could try installing the Windows drivers under Wine. Not saying it's perfect, but worth a shot.

Another idea: Have you tried enabling PulseAudio?

I know PulseAudio is installed by default, however not sure how to enable it in Mint Linux 8

---

### Post by MasterNetra on 2010-01-24
*Bump Unresolved*

---

### Post by MasterNetra on 2010-05-23
bumped again this is still unresolved. Using Open Suse 11.2 on the laptop now sense Lucid nor its derivitives will even load.

---

### Post by BARlotta on 2010-08-21
I got sound working on ubuntu 9.10 on the same gateway machine.  Did 3 things:
1. made sure user had "Use Audio Devices" privledge (i don't think this was it)
2. Under Sound Preferences, the Output tab, change the Connector drop down to one of the Unamplified settings : "Analog Output / No Amplifier"
3. I installed the "linux-backports-modules-alsa-karmic-generic" package

---

### Post by MasterNetra on 2010-08-26
> **BARlotta said:**
> I got sound working on ubuntu 9.10 on the same gateway machine.  Did 3 things:
1. made sure user had "Use Audio Devices" privledge (i don't think this was it)
2. Under Sound Preferences, the Output tab, change the Connector drop down to one of the Unamplified settings : "Analog Output / No Amplifier"
3. I installed the "linux-backports-modules-alsa-karmic-generic" package

Thanks!... to bad the screen on my sister inlaws laptop went out. Or I would of gotten that taken cared off.

---

