---
title: "TASCAM US-122L in Maverick Meerkat 10.10, 64-bit - Sony Vaio VPCF1"
date: 2011-03-04
forum: Hardware
---

### Post by signal1980 on 2011-03-04
Hello. Thanks for looking in.

Trying to install the Tascam US-122L on Sony VPCF1 (64-bit - 4Gb RAM), running Ubuntu 10.10 Maverick Meerkat 64-bit.

Have searched the recommended guides, but my problem appears to occur before these guides can be followed.

Complete noob, but, so far, entering:

 cat /proc/asound/modules

...into the terminal, returns:

 0 snd_hda_intel
 1 snd_hda_intel

...while the Tascam is plugged-in. 

Also,

alsa-tools, alsa-firmware, alsa-firmware-loaders 

...are, according to Synaptic, all installed.

Am willing to donate limbs to a good cause for any help offered.

Many thanks x

---

### Post by Feareilo on 2011-03-21
I am having the same problem. I think it might be related with the firmware. I upgraded my US-122L to the latest firmware and drivers in Windows. Now I want to use it in Ubuntu but it is not working. The Briata walkthrough seemed very easy... but the unit is not recognized in proc/asound/modules and nothing seems to work. If you ever get around this, please share how you did.

---

### Post by Feareilo on 2011-03-31
Just to let everyone know, I downloaded and downgraded to the oldest firmware (0.2, I think) using Win*dose* XP and guess what... Ubuntu 10.04 64bit recognized the card! I haven't thoroughly tested it as this is not the computer I want to use it in. However, I think this is a relevant finding. Hope it helps you.

---

### Post by deoanam2002 on 2011-12-19
Hi Feareilo,
How did you downgrade the firmware? I can't seem to find an old firmware file.
Thanks.

> **Feareilo said:**
> Just to let everyone know, I downloaded and downgraded to the oldest firmware (0.2, I think) using Win*dose* XP and guess what... Ubuntu 10.04 64bit recognized the card! I haven't thoroughly tested it as this is not the computer I want to use it in. However, I think this is a relevant finding. Hope it helps you.

---

