---
title: "Alsa"
date: 2008-02-15
forum: Hardware &amp; Laptops
---

### Post by petersra on 2008-02-15
The Gusty kernel comes with the ALSA modules.  So, how can I specify a specific sound driver be loaded at boot time?

---

### Post by wirawan0 on 2008-02-15
When you installed it, it should have been automatically determined. Did you not have sound? Did you check tha the volume and speakers are all OK? Can you open up the volume control and slide the volume up and down?

Another check: open terminal, and  type: 

  ls -l /proc/asound

Let us know what you found. You should cat /proc/asound/cards and /proc/asound/devices to see if your devices are recognized.

Wirawan

---

### Post by petersra on 2008-02-15
Thanks for the reply.  I have an Extreme FX Souindblaster that is not recognized.  I have compiled the ALSA driver CA0106 and it works.  However, every time there is a kernel update I get symbol mismatches.  So, I see that ALSA is already in the Gusty kernel so am looking for a way to load the correct sound modules/drivers.

Rob

---

### Post by Yellow Pasque on 2008-02-15
First, make sure it's not already loading at boot. Try this after you boot:
```
lsmod | grep 106
```
Now, make sure the module can load without issue:
```
sudo modprobe -v snd-card-ca0106
```
If that works, add 'snd-card-ca0106' to the /etc/modules file.

Also, make sure these moduleas are being loaded for OSS emulation:
snd-pcm-oss ; snd-mixer-oss ; snd-seq-oss

---

