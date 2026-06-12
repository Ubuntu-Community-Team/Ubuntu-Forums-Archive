---
title: "audio initially worked, now it doesn't after upgrade"
date: 2011-04-04
forum: Hardware
---

### Post by Beaker McChemist on 2011-04-04
I have a msi wind u100 netbook currently running Xubuntu 10.10 and I do not have any audio.  I initially installed Xubuntu 9.10 and the audio worked perfectly "out of the box".
At some point, I don't know exactly when, after upgrading to 10.10, downloading lots of packages, and trying to install some software from source, I now have no sound being produced by my machine.  I have searched through the forums and tried all kinds of things and nothing has worked so far.  I feel like there is something obvious I am missing but I can't figure it out. I suppose I could do a fresh reinstall of 9.10 but I am trying to avoid that. Any suggestions on what to try next?

Here are the output from several of the suggestions.
I did:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

Followed by:

sudo apt-get install linux-sound-base alsa-base alsa-utils


lsusb -v gives me:

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
    Subsystem: Micro-Star International Co., Ltd. Device 0110
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at ffe00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

aplay -l gives me:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

groups gives me:

adm dialout cdrom audio plugdev lpadmin admin sambashare

Under xfce4-mixer in settings editor it says:
sound card    RealtekALC1200OSMixer
                    HDAIntelAlsamixer
active card    HDAIntelAlsamixer

---

### Post by lidex on 2011-04-05
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Beaker McChemist on 2011-04-05
Here you go. 

[http://www.alsa-project.org/db/?f=7d8deedd990511c07865f5bb4f3345b66cfb35f9](http://www.alsa-project.org/db/?f=7d8deedd990511c07865f5bb4f3345b66cfb35f9)
Thanks for replying so promptly.

---

### Post by lidex on 2011-04-05
Xubuntu uses pulseaudio?
Try resetting your pulse configuration.
```

rm -r ~/.pulse ~/.pulse-cookie 

```
**Reboot**

No help? 
```
echo "options snd-hda-intel model=3stack-6ch-dig" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by Beaker McChemist on 2011-04-06
Neither of these worked.  Thank you for your help.  I think I will just have to reinstall and be more carefull about what I try to install.  I know enough to get myself in trouble but not enough to get myself out.

Thanks again.

---

