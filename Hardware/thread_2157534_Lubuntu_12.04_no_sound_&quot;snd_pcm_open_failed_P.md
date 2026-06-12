---
title: "Lubuntu 12.04: no sound &quot;snd_pcm_open failed: Permission denied.&quot;"
date: 2013-06-25
forum: Hardware
---

### Post by sanderj on 2013-06-25
With a fresh install of Lubuntu 12.04 on older hardware, I have no sound (running as normal user), and I get the errors below:


Audacious says:

> ALSA error:
snd_pcm_open failed: Permission denied.

When I run audacious as root, it works and I get sound.

```
sudo audacious 
```

So ... which setting / right is not set right? 


VLC says:

> Audio output failed:
The audio device "default" could not be used:
Permission denied.

lspci -vv says:
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Gateway 2000 Device 016a
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 46
	Region 0: Memory at 58300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

```

Snippets from dmesg:

```
sander@eMachines:~$ dmesg | grep snd
[    7.740857] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    7.740923] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[    7.740956] snd_hda_intel 0000:00:1b.0: setting latency timer to 64

sander@eMachines:~$ dmesg | grep sound
[    8.437118] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[    8.437362] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
sander@eMachines:~$
```


EDIT:

VLC from the command line gives this:

```
[0x8af93b0] pulse audio output error: PulseAudio server connection failure: Connection refused
ALSA lib pcm_dmix.c:985:(snd_pcm_dmix_open) unable to create IPC semaphore
[0x8af93b0] alsa audio output error: cannot open ALSA device "default": Permission denied
[0x8af93b0] oss audio output error: cannot open audio device (/dev/dsp)
[0x8af93b0] main audio output error: no suitable audio output module
[0xb5b51e08] main decoder error: failed to create audio output
```

and a check:

```
sander@eMachines:~$ ll /dev/dsp
ls: cannot access /dev/dsp: No such file or directory
sander@eMachines:~$
```

---

### Post by sanderj on 2013-06-25
Never mind ... a good old reboot solved it. Strange.

---

