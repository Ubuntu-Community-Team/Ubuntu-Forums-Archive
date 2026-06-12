---
title: "DVB-S2 help"
date: 2016-01-12
forum: Hardware
---

### Post by chris-dj-tye on 2016-01-12
Hi all,

Having a few problems with my new DVB-S2 tuner.

I used to use Ubuntu many years ago, and have recently gotten back into it (the RPi helped). Anyway, I recently purchased a DVB-S2 tuner, which according to linuxtv.org should be compatible.[ Here is the page on my device]("http://www.linuxtv.org/wiki/index.php/TechnoTrend_TT-connect_S2-4600").

It says that it is supported natively since kernel 4.2. The command "uname -r" shows that I have version "4.2.0-19-generic".

TVHeadEnd can't find the device, and I can't seem to scan with it using any command line tools.

lsusb hangs and won't display anything (waited 20 minutes).

dmesg | grep dvb shows this:
```
[   19.225228] dvb-usb: found a 'TechnoTrend TT-connect S2-4600' in warm state.[   19.225446] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   19.230026] dvb-usb: MAC address: bc:ea:2b:46:0a:0a
[   19.884404] Modules linked in: m88ds3103 i2c_mux dvb_usb_dw2102(+) dvb_usb dvb_core rc_core snd_hda_codec_hdmi snd_hda_codec_analog snd_hda_codec_generic arc4 iwldvm uvcvideo snd_hda_intel videobuf2_vmalloc mac80211 snd_hda_codec videobuf2_memops snd_hda_core videobuf2_core snd_hwdep v4l2_common videodev snd_pcm media iwlwifi snd_seq_midi hp_wmi snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device sparse_keymap snd_timer snd coretemp lpc_ich joydev input_leds soundcore cfg80211 serio_raw hp_accel shpchp lis3lv02d 8250_fintek input_polldev mac_hid parport_pc ppdev lp parport autofs4 uas usb_storage i915 psmouse ahci libahci sky2 i2c_algo_bit drm_kms_helper drm video wmi
[   19.886067]  [<f88e645c>] tt_s2_4600_frontend_attach+0x18c/0x330 [dvb_usb_dw2102]
[   19.886130]  [<f88ce64a>] dvb_usb_adapter_frontend_init+0xba/0x160 [dvb_usb]
[   19.886189]  [<f88ce48e>] ? dvb_usb_adapter_dvb_init+0x13e/0x1e0 [dvb_usb]
[   19.886248]  [<f88cd964>] dvb_usb_device_init+0x454/0x6a0 [dvb_usb]
[   19.886301]  [<f88e4510>] dw2102_probe+0x330/0x3b0 [dvb_usb_dw2102]
[   19.888172]  [<f85d0017>] dw2102_driver_init+0x17/0x1000 [dvb_usb_dw2102]

```

I've done a lot of hunting around on the internet, and it is a bit of a minefield!

If anyone has any suggestions, they would be most welcome!

Regards,
Chris

---

