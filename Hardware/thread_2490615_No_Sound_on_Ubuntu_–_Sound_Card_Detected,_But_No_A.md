---
title: "No Sound on Ubuntu – Sound Card Detected, But No Audio (Intel 51c)"
date: 2023-09-09
forum: Hardware
---

### Post by ikxs on 2023-09-09
Hello,
I recently purchased a new laptop, the LG Gram 16, and installed Ubuntu on it, but I'm having trouble getting the sound to work. Here are the steps I've taken so far:
In the sound settings, everything appears to be fine, but the test sound remains silent.


Software and Driver Check:

[LIST]
[*]Ubuntu recognizes the sound card using the lspci | grep -i Audio command:
makefile


[/LIST]
00:1f.3 Multimedia audio controller: Intel Corporation Device 51ca (rev 01)




The "sof-audio-pci-intel-tgl" driver appears to be loaded successfully (to my amateur eyes) according to the dmesg logs.

less



[LIST]
[*]sudo dmesg | grep -i audio
    [sudo] password for alex:
    [    5.434109] sof-audio-pci-intel-tgl 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if info 0x040100
    [    5.434141] sof-audio-pci-intel-tgl 0000:00:1f.3: Digital mics found on Skylake+ platform, using SOF driver
    [    5.434158] sof-audio-pci-intel-tgl 0000:00:1f.3: enabling device (0000 -> 0002)
    [    5.434801] sof-audio-pci-intel-tgl 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if 0x040100
    [    6.847479] sof-audio-pci-intel-tgl 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
    [    6.907724] sof-audio-pci-intel-tgl 0000:00:1f.3: use msi interrupt mode
    [    6.969063] sof-audio-pci-intel-tgl 0000:00:1f.3: hda codecs found, mask 5
    [    6.969066] sof-audio-pci-intel-tgl 0000:00:1f.3: using HDA machine driver skl_hda_dsp_generic now
    [    6.969070] sof-audio-pci-intel-tgl 0000:00:1f.3: DMICs detected in NHLT tables: 2
    [    6.970040] sof-audio-pci-intel-tgl 0000:00:1f.3: Firmware info: version 2:2:0-57864
    [    6.970043] sof-audio-pci-intel-tgl 0000:00:1f.3: Firmware: ABI 3:22:1 Kernel ABI 3:23:0
    [    6.970047] sof-audio-pci-intel-tgl 0000:00:1f.3: unknown sof_ext_man header type 3 size 0x30
    [    7.064868] sof-audio-pci-intel-tgl 0000:00:1f.3: Firmware info: version 2:2:0-57864
    [    7.064873] sof-audio-pci-intel-tgl 0000:00:1f.3: Firmware: ABI 3:22:1 Kernel ABI 3:23:0
    [    7.082722] sof-audio-pci-intel-tgl 0000:00:1f.3: Topology: ABI 3:22:1 Kernel ABI 3:23:0
    [    7.114342] snd_hda_codec_realtek ehdaudio0D0: autoconfig for ALC298: line_outs=1 (0x17/0x0/0x0/0x0/0x0) type:speaker
    [    7.114352] snd_hda_codec_realtek ehdaudio0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
    [    7.114353] snd_hda_codec_realtek ehdaudio0D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
    [    7.114355] snd_hda_codec_realtek ehdaudio0D0:    mono: mono_out=0x0
    [    7.114356] snd_hda_codec_realtek ehdaudio0D0:    inputs:
    [    7.114357] snd_hda_codec_realtek ehdaudio0D0:      Mic=0x18
    [    7.164311] snd_hda_codec_realtek ehdaudio0D0: ASoC: sink widget AIF1TX overwritten
    [    7.164320] snd_hda_codec_realtek ehdaudio0D0: ASoC: source widget AIF1RX overwritten




[/LIST]
Despite all attempts, I'm still not getting any sound.
Could someone please assist me in further diagnosing and resolving this issue? Are there additional steps or solutions I should try?

Here are additional details about my system:

[LIST]
[*]Ubuntu Version: 23.04
[*]Sound Card: Intel Corporation Device 51ca (rev 01)
[/LIST]
Thank you in advance for your help!

Alex

---

### Post by TheFu on 2023-09-09
[LIST=1]
[*]install **pavucontrol**.
[*]Play around with the settings on each tab. I like to start from the far right tab, Configuration, enable only the 1 output I want, disable all the others.
[*]Work left in the tabs. Ensure the outputs are consistently set.  Look for 80-100%   Ignore "inputs" and "recording" tabs, for now.
[*]On the output tab, choose the built-in speakers, set to 80-100%.
[*]On the Playback tab, nothing will show up until there is some software trying to play something.  Use any application you like.  You may need to switch to a different tab, start playback, then switch back to the "Playback" tab to see the monitor for that application moving.  Set the volume out to be 80-100%. If there's no bar moving, then the wrong output is selected or the system is set for mute.
[/LIST]


Be happy.

---

### Post by arnaud380 on 2023-09-19
Hello, 

I'have the same issue with my LG gram
All info are the same than Ikxs.

The manipulation propsed by TheFu doesn't work for me.

Thank you

---

### Post by bengao51 on 2023-09-20
I also tried TheFu's suggestion, it doesn't work for me either

---

