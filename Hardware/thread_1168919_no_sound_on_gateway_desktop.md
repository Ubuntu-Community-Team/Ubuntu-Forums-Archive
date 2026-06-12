---
title: "no sound on gateway desktop"
date: 2009-05-24
forum: Hardware
---

### Post by ronol on 2009-05-24
Hello! relative newbie here with a sound issue. I have searched the forums with no luck. I have checked the alsa mixer and it is unmuted. Here is my aplay-l and lspci -v

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
lspci -v
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
	Subsystem: Gateway 2000 Device 604e
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d0000000-d2ffffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Gateway 2000 Device 604e
	Flags: bus master, fast devsel, latency 0, IRQ 2296
	Memory at d3300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
I had the same problem in the last version and hoped upgrading would solve it. Any ideas?

---

### Post by cwsnyder on 2009-05-24
First, are you using ALSA or Pulse-Audio?  Pulse-Audio has been the default since Hardy Heron, but that can break some of the older audio software/cause some of the older audio software to break your pulse-audio install.  In particular, installing JACK software can cause your audio system to break. :(

That said, you can use either Pulse-Audio type applications, or you can use ALSA based applications, just be consistent.

If you want to use Pulse-Audio, [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578") is the most comprehensive solution guide I found.

If you want to use ALSA, [Comprehensive Sound Problem Solutions]("http://ubuntuforums.org/showthread.php?t=205449") is probably the best guide.

---

