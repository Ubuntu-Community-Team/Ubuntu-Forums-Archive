---
title: "How do I reinstall my sound driver(s)?"
date: 2020-07-10
forum: Hardware
---

### Post by stevermann on 2020-07-10
I originally installed Ubuntu Server (V18.04) on a new Intel Nuc, and later (after installing my programs and databases) decided that I would rather have the desktop version. So I installed ubuntu-desktop over the server using these steps:
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo reboot

```

Everything works fine, however, I have no sound from the headphone jack.


I installed pavucontrol and on the Output Devices tab:
**port: "Dummy Output"**


So, would reinstalling the audio drivers fix this, or should I consider starting over and install Ubuntu Desktop?


Here is some of the diagnostics I used:
```
lspci -v | grep -i -A7 audio
00:1f.3 Audio device: Intel Corporation Device 9dc8 (rev 30) (prog-if 80)
    Subsystem: Intel Corporation Device 2074
    Flags: bus master, fast devsel, latency 32, IRQ 143
    Memory at c0b20000 (64-bit, non-prefetchable) [size=16K]
    Memory at 404ab00000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, sof_pci_dev

```

---

### Post by Yellow Pasque on 2020-07-11
Try creating a new user and see if they have sound.

---

