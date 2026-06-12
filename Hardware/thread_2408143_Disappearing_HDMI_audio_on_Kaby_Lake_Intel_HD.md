---
title: "Disappearing HDMI audio on Kaby Lake Intel HD"
date: 2018-12-14
forum: Hardware
---

### Post by rustyx2 on 2018-12-14
After an upgrade from kernel 4.4.0-101 to 4.4.0-140 the Intel HD audio is disappearing after 30-40 minutes.

(so that's on 16.04.  On 18.04 there is no sound whatsoever, snd_hda_intel is NOT detected at boot at all)


root@htpc2:~# cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version k4.4.0-140-generic.

root@htpc2:~# cat /proc/asound/modules
 0 snd_hda_intel

root@htpc2:~# cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xdf140000 irq 135

root@htpc2:~# cat /var/log/kern.log | grep -iE "(hda|snd)"
Dec 10 21:17:59 htpc2 kernel: [    3.233565] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915_bpo])
Dec 10 21:17:59 htpc2 kernel: [    3.281905] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC892: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
Dec 10 21:17:59 htpc2 kernel: [    3.281907] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
Dec 10 21:17:59 htpc2 kernel: [    3.281909] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
Dec 10 21:17:59 htpc2 kernel: [    3.281910] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
Dec 10 21:17:59 htpc2 kernel: [    3.281911] snd_hda_codec_realtek hdaudioC0D0:    inputs:
Dec 10 21:17:59 htpc2 kernel: [    3.281912] snd_hda_codec_realtek hdaudioC0D0:      Front Mic=0x19
Dec 10 21:17:59 htpc2 kernel: [    3.281913] snd_hda_codec_realtek hdaudioC0D0:      Rear Mic=0x18
Dec 10 21:17:59 htpc2 kernel: [    3.281914] snd_hda_codec_realtek hdaudioC0D0:      Line=0x1a
Dec 10 21:17:59 htpc2 kernel: [    3.309908] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input12
Dec 10 21:17:59 htpc2 kernel: [    3.339019] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1f.3/sound/card0/input13
Dec 10 21:17:59 htpc2 kernel: [    3.339051] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1f.3/sound/card0/input14
Dec 10 21:17:59 htpc2 kernel: [    3.339082] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input15
Dec 10 21:17:59 htpc2 kernel: [    3.339110] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input16
Dec 10 21:17:59 htpc2 kernel: [    3.339145] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input17

<... I have sound!  ... but for about 1/2 hour .... >

Dec 10 21:48:11 htpc2 kernel: [ 1816.482495] snd_hda_intel 0000:00:1f.3: azx_get_response timeout, switching to polling mode: last cmd=0x20170503
Dec 10 21:48:12 htpc2 kernel: [ 1817.490389] snd_hda_intel 0000:00:1f.3: No response from codec, disabling MSI: last cmd=0x20170503
Dec 10 21:48:13 htpc2 kernel: [ 1818.498283] snd_hda_intel 0000:00:1f.3: azx_get_response timeout, switching to single_cmd mode: last cmd=0x20170503
Dec 10 23:09:05 htpc2 kernel: [ 6669.161420] snd_hda_codec_hdmi hdaudioC0D2: Unable to sync register 0x2f0d00. -5
Dec 10 23:09:05 htpc2 kernel: [ 6669.161597] snd_hda_codec_hdmi hdaudioC0D2: HDMI: invalid ELD buf size -1
Dec 10 23:09:05 htpc2 kernel: [ 6669.161770] snd_hda_codec_hdmi hdaudioC0D2: HDMI: invalid ELD buf size -1
Dec 10 23:09:05 htpc2 kernel: [ 6669.161941] snd_hda_codec_hdmi hdaudioC0D2: HDMI: invalid ELD buf size -1
Dec 10 23:09:05 htpc2 kernel: [ 6669.162028] snd_hda_codec_hdmi hdaudioC0D2: HDMI: invalid ELD buf size -1
Dec 10 23:09:05 htpc2 kernel: [ 6669.461029] snd_hda_codec_hdmi hdaudioC0D2: HDMI: invalid ELD buf size -1
Dec 10 23:09:05 htpc2 kernel: [ 6669.461157] snd_hda_codec_hdmi hdaudioC0D2: HDMI: invalid ELD buf size -1
Dec 10 23:09:05 htpc2 kernel: [ 6669.461279] snd_hda_codec_hdmi hdaudioC0D2: HDMI: invalid ELD buf size -1
Dec 10 23:09:05 htpc2 kernel: [ 6669.761003] snd_hda_codec_hdmi hdaudioC0D2: HDMI: invalid ELD buf size -1
Dec 10 23:09:05 htpc2 kernel: [ 6669.761131] snd_hda_codec_hdmi hdaudioC0D2: HDMI: invalid ELD buf size -1
Dec 10 23:09:05 htpc2 kernel: [ 6669.761253] snd_hda_codec_hdmi hdaudioC0D2: HDMI: invalid ELD buf size -1

root@htpc2:~# cat /proc/asound/cards
--- no soundcards ---


Seems to be related to this issue in the i915 driver:
[https://bugs.freedesktop.org/show_bug.cgi?id=104952](https://bugs.freedesktop.org/show_bug.cgi?id=104952)

Question is - when will that fix be merged into ubuntu?

---

