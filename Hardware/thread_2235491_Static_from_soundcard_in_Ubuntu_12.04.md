---
title: "Static from soundcard in Ubuntu 12.04"
date: 2014-07-21
forum: Hardware
---

### Post by knight69 on 2014-07-21
I just installed Ubuntu 12.04 (kernel version 3.13.0-32) on a new desktop with a Gigabyte GA-Z97X-SLI motherboard with onboard sound and Realtek ALC1150 codec.  This is a dual boot system also running Windows 7 pro.  Under Windows the sound system is perfect.  Under linux I get only static, the volume of which is proportional to the sound level.  The audio report I returned from lspci is as follows

00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
    Subsystem: Intel Corporation Device 2010
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 48
    Region 0: Memory at f7c34000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel


00:1b.0 Audio device: Intel Corporation Device 8ca0
    Subsystem: Gigabyte Technology Co., Ltd Device a182
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 47
    Region 0: Memory at f7c30000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel 

DKMS is installed.
I reinstalled PulseAudio using the Synaptic package manager
I resinstalled Alsa Base and Alsa Utils
I tried to follow the instructions at [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS), but it only goes to kernel version 3.8 (I have 3.13 installed)

Anyone have any other ideas?

---

### Post by Yellow Pasque on 2014-07-21
```
echo "options snd-hda-intel vid=8086 pid=8ca0 snoop=0" | sudo tee /etc/modprobe.d/fix-sound-intel97.conf
sudo alsa force-reload
pulseaudio -k
```

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1321421](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1321421)

---

