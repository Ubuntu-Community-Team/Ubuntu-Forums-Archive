---
title: "No audio functions with fglrx drivers and AMD video card, Ubuntu 14.04"
date: 2016-01-09
forum: Hardware
---

### Post by james191 on 2016-01-09
**Edit: After some further searching I tried simply installing Ubuntu 15.10 and the issue was no longer present**

Hello,

I recently put together a new computer, and installed Ubuntu 14.04 as the sole operating system for the device. When ubuntu was first installed, the graphics card I included in the machine (a Radeon R7 370) was unable to properly display Ubuntu, so I was forced to disable it and use the intergrated graphics on my CPU instead for a while. During this time there were no audio issues and every device I attempted using fuctioned correctly.

In order to make the graphics card function correctly, I installed the proprietary fglrx drivers via the 'additional drivers' menu. Once this process was completed, and the GPU was reactivated, it functioned correctly and there have been no display issues whatsoever since. However, immediately after doing this, the audio on the computer stopped functioning properly; none of the external devices I attempted using functioned correctly, and the 'Sound Settings' menu displayed no audio devices whatsoever, not even a 'Dummy' device, no matter what was plugged in, or where.

I've done some searching around the internet myself, hoping to find a solution, but haven't had any success. I fiddled around in the BIOS trying to see if I had to enable the built in sound card manually, but I couldn't find any appropriate options and had no luck. However, when doing some of the checks and tests that were recommended online, I found some interesting information:

The command:

```
lspci -v | grep -A7 -i "audio"
```

Properly identifies both the built in sound device on the motherboard, and the HDMI audio device on the GPU:

```
00:1f.3 Audio device: Intel Corporation Device a170 (rev 31)
    Subsystem: Gigabyte Technology Co., Ltd Device a182
    Flags: fast devsel, IRQ 16
    Memory at dff20000 (64-bit, non-prefetchable) [size=16K]
    Memory at dff00000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

--
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
    Subsystem: ASUSTeK Computer Inc. Device aab0
    Flags: bus master, fast devsel, latency 0, IRQ 126
    Memory at dfe60000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

```

However, alsa command:

```
aplay -l
```

Only lists devices associated with the GPU:

```
**** List of PLAYBACK Hardware Devices ****
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 11: HDMI 5 [HDMI 5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

And upon checking alsamixer, I was unable to choose to use any sound device other than the HDMI card on the GPU, and alsamixer didn't list any other sound devices as being installed. It seems as though alsa is for some reason unable to detect the intel sound device on the motherboard, so it's stuck trying to use the HDMI device on the graphics card for which I have no compatible output devices that I could even use to test if this functions correctly.

At this point I'm unsure of how I should proceed troubleshooting, I haphazardly tried following a few guides to reinstall or reset alsa that I found online, but none of then achieved anything. Any advice in any possible direction towards identifying or solving this problem would be greatly appreciated.

Thanks.

**Edit: After some further searching I tried simply installing Ubuntu 15.10 and the issue was no longer present**

---

