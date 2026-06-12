---
title: "Garmin GPS 18 (puck) and GPSD"
date: 2010-05-07
forum: Hardware
---

### Post by YogiPaolo on 2010-05-07
I am having massive puzzling frustration in trying to get my Garmin GPS 18 USB receiver working under 10.4 netbook remix on an EEEPC 1008HA. This is the "hockey puck" garmin device.

I can only get /dev/ttyUSB0 to appear by manually loading the garmin_usb module using modprobe.

This module is blacklisted for a reason unknown to me. 

After loading the module and restarting gpsd, i can see a skymap with xgps and see satellites listed with cgps. It looks like the device is recognized and data is flowing. However, both tools show no fix and no location information. Also, the date and time are way off. The year shows 1970.

I have tried changing to NMEA mode using gpsctl. No love.

The device seems to pick up sats, but no fix. 

```
Here are some particulars:

laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux
```


```
Bus 002 Device 003: ID 091e:0003 Garmin International GPSmap (various models)
```

```
May  7 00:08:43 paolo-laptop kernel: [  176.728755] garmin_gps ttyUSB0: Garmin GPS usb/tty converter now disconnected from ttyUSB0
May  7 00:08:43 paolo-laptop kernel: [  176.728828] garmin_gps 2-2:1.0: device disconnected
May  7 00:08:48 paolo-laptop kernel: [  181.552105] usb 2-2: new full speed USB device using uhci_hcd and address 3
May  7 00:08:48 paolo-laptop kernel: [  181.772655] usb 2-2: configuration #1 chosen from 1 choice
May  7 00:08:48 paolo-laptop kernel: [  181.775601] garmin_gps 2-2:1.0: Garmin GPS usb/tty converter detected
May  7 00:08:48 paolo-laptop kernel: [  181.775862] usb 2-2: Garmin GPS usb/tty converter now attached to ttyUSB0
```

```

Module                  Size  Used by
garmin_gps             14947  1 
usbserial              33019  3 garmin_gps
binfmt_misc             6587  1 
ppdev                   5259  0 
nls_iso8859_1           3249  2 
nls_cp437               4919  2 
vfat                    8901  2 
fat                    47767  1 vfat
snd_hda_codec_realtek   203168  1 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
softcursor              1189  1 bitblit
vga16fb                11385  0 
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
vgastate                8961  1 vga16fb
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
joydev                  8708  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
arc4                    1153  2 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
ath9k                 306010  0 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i915                  282354  4 
uvcvideo               56990  0 
mac80211              204922  1 ath9k
drm_kms_helper         29297  1 i915
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm                   162471  5 i915,drm_kms_helper
videodev               34361  1 uvcvideo
ath                     7611  1 ath9k
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              24177  2 i915
v4l1_compat            13251  2 uvcvideo,videodev
soundcore               6620  1 snd
atl1c                  28083  0 
agpgart                31724  2 drm,intel_agp
cfg80211              126485  3 ath9k,mac80211,ath
i2c_algo_bit            5028  1 i915
led_class               2864  1 ath9k
psmouse                63245  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
video                  17375  1 i915
serio_raw               3978  0 
eeepc_laptop           12847  0 
output                  1871  1 video
parport                32635  2 ppdev,lp
usb_storage            39425  1 
ahci                   32008  4 
```


Any help is greatly appreciated.

---

### Post by YogiPaolo on 2010-05-16
no takers...

---

### Post by benguin on 2010-08-08
Hey there,
Just came across your post searching for gpsd troubles. I can't even get gpsd to stream data from the puck gps module in Karmic, whereas the same hardware setup works out of the box in Lucid. What other tools have you tried (other than xgps and cgps), if I may inquire so ?

Regards,
J

---

