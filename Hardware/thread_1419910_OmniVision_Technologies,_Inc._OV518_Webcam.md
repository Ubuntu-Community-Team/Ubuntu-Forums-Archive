---
title: "OmniVision Technologies, Inc. OV518 Webcam"
date: 2010-03-02
forum: Hardware
---

### Post by manolomanolo on 2010-03-02
Hi to all.

I am unable to make my webcam work with skype
It does not work with Camorama but it works with Cheese.

When testing it with Skype I can only see a green image.

That's the dmesg:
```
**dmesg | tail -20**
[   71.321875] sr1: scsi-1 drive
[   71.322173] sr 5:0:0:0: Attached scsi CD-ROM sr1
[   71.322354] sr 5:0:0:0: Attached scsi generic sg2 type 5
[   79.842458] ISO 9660 Extensions: Microsoft Joliet Level 3
[   79.853468] ISOFS: changing to secondary root
[  133.397828] PPP BSD Compression module registered
[  133.411482] PPP Deflate Compression module registered
[  479.524062] usb 2-1: new full speed USB device using uhci_hcd and address 2
[  479.740279] usb 2-1: configuration #1 chosen from 1 choice
[  480.444581] Linux video capture interface: v2.00
[  480.478513] gspca: main v2.6.0 registered
[  480.497204] gspca: probing 05a9:0518
[  480.499034] ov519: Device revision 1
[  480.584451] ov519: Uploading quantization tables
[  483.365513] ov519: I2C synced in 0 attempt(s)
[  483.365524] ov519: starting OV6xx0 configuration
[  483.388430] ov519: Sensor is an OV66308AF
[  484.188434] gspca: probe ok
[  484.188487] usbcore: registered new interface driver ov519
[  484.188496] ov519: registered

```

```
**lsusb | grep Omni**
Bus 002 Device 002: ID 05a9:0518 OmniVision Technologies, Inc. OV518 Webcam
```

```
**lsmod**
Module                  Size  Used by
gspca_ov519            25440  0 
gspca_main             22812  1 gspca_ov519
videodev               36736  1 gspca_main
v4l1_compat            14496  1 videodev
ppp_deflate             4732  0 
zlib_deflate           20088  1 ppp_deflate
bsd_comp                5436  0 
ppp_async               8860  1 
crc_ccitt               1852  1 ppp_async
nls_utf8                1568  1 
isofs                  31620  1 
option                 23232  1 
usbserial              36264  4 option
usb_storage            52576  1 
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
joydev                 10240  0 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
iptable_filter          3100  0 
snd_seq_dummy           2656  0 
pcmcia                 36808  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ipw2200               140292  0 
libipw                 43148  1 ipw2200
lib80211                6432  2 ipw2200,libipw
yenta_socket           24296  2 
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                56500  0 
serio_raw               5280  0 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
shpchp                 32272  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
8139too                22620  0 
8139cp                 19260  0 
mii                     5212  2 8139too,8139cp
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
video                  19380  0 
output                  2780  1 video
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
intel_agp              27484  1 
agpgart                34988  3 ttm,drm,intel_agp
```

Any suggestion  please?
Thanks.

---

### Post by manolomanolo on 2010-03-06
Still no answer?

---

### Post by nikkkko on 2010-03-09
Hi,

Is this a Dell computer by any chance?  I have a Dell with a OV2640 Webcam which stopped working after an upgrade on Karmic about a week ago. I have regular contact with someone who is also on a Dell, also on Karmic and whose webcam failed at the same time as me.

Did you get to the bottom of this?

---

### Post by gordintoronto on 2010-03-09
Try starting Skype with this command:
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

---

### Post by nikkkko on 2010-03-09
I came home this evening, rebooted my laptop and installed Cheese to see if it could see the webcam.  It could.  Then I ran Skype and it found the webcam too.

Are these two events related?  I don't know, but if my contact with the Dell has the same experience, I'll let you know.

---

