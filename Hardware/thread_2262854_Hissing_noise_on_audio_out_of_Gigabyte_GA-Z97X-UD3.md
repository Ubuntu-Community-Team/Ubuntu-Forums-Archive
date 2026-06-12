---
title: "Hissing noise on audio out of Gigabyte GA-Z97X-UD3H (Intel HDA with Realtek codec)"
date: 2015-01-27
forum: Hardware
---

### Post by toldbury on 2015-01-27
I have a computer with a Gigabyte GA-Z97X-UD3H main board. On Windows 7 the sound is perfect with no hissing. On Ubuntu (14.04) I'm experiencing a persistent hissing noise on the audio. The sound is still audible on top of this but the noise is persistent unless the sound is muted from within Ubuntu.   The hissing makes the audio pretty difficult to use, as it's very loud, it's definitely not what would be expected from a working sound driver.

To my non-expert ears it sounds a little like the gain is set to maximum on the amplifier/DAC, and the software is scaling the volume, rather than the DAC, hence why there's so much noise. But I don't know for sure, I don't write sound card drivers.

lspci: ```
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:14.0 USB controller: Intel Corporation Device 8cb1
00:16.0 Communication controller: Intel Corporation Device 8cba
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-V
00:1a.0 USB controller: Intel Corporation Device 8cad
00:1b.0 Audio device: Intel Corporation Device 8ca0
00:1c.0 PCI bridge: Intel Corporation Device 8c90 (rev d0)
00:1c.3 PCI bridge: Intel Corporation Device 8c96 (rev d0)
00:1d.0 USB controller: Intel Corporation Device 8ca6
00:1f.0 ISA bridge: Intel Corporation Device 8cc4
00:1f.2 SATA controller: Intel Corporation Device 8c82
00:1f.3 SMBus: Intel Corporation Device 8ca2
01:00.0 VGA compatible controller: NVIDIA Corporation GK107 [GeForce GTX 650] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GK107 HDMI Audio Controller (rev a1)
03:00.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 41)
```

lsusb:```
Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 003 Device 002: ID 03f0:0f0c Hewlett-Packard Wireless Keyboard and Optical Mouse receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

A dmesg about sound, maybe related?
```
[    5.626004] snd_hda_intel 0000:00:1b.0: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
```

Thanks for any suggestions

---

### Post by Yellow Pasque on 2015-01-29
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1321421](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1321421)

Either use the workaround command in the bug report or upgrade the sound module: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by toldbury on 2015-01-31
I've tried those, no luck.

I should reiterate that the sound is usable, there's just too much noise. The sound is not distorted, and if the audio is loud enough you would not know about the noise.

Is there any low-level way to control the gain of the DACs in the sound chipset? That's not just using alsamixer, I want direct control, if possible, because all it sounds like to me is that DAC gain is set too high.

I've also tried turning off line in audio, by setting all gains to zero from alsamixer, no dice.

---

### Post by Yellow Pasque on 2015-01-31
There is hda-verb:
```
sudo apt-get install alsa-tools
hda-verb -L
```

There is also hda-analyzer:
```
cd ~/
wget http://www.alsa-project.org/hda-analyzer.py
sudo python hda-analyzer.py
```

---

### Post by toldbury on 2015-02-01
THANKS!

I fixed it... not sure if permanent though.

Used hda-anaylser.py, node 0x0c AUD_MIX I muted Val[2],Val[3] - I am guessing these are mix-in or line-in inputs getting mixed into the output.

Noise free, perfect audio! :)

Is it worth raising a bug on Launchpad to get this fixed for future releases?

---

### Post by mörgæs on 2015-02-02
According to the bug report it's fixed in 15.04. Would be good if you could check it on your hardware.

---

### Post by toldbury on 2015-02-02
Only problem is -- it's not persistent. I have to do this on every boot.

> **mörgæs said:**
> According to the bug report it's fixed in 15.04. Would be good if you could check it on your hardware.

I will see if I can do that. Is there an easy way without reinstalling? I can't reinstall Ubuntu right now.

---

### Post by mörgæs on 2015-02-02
A live boot will do.

---

