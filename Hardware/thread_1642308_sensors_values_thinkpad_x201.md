---
title: "sensors values thinkpad x201"
date: 2010-12-10
forum: Hardware
---

### Post by chik3n on 2010-12-10
Hi,

(this post has been posted in german at ubuntuusers.de as well)

I am the proud owner of a thinkpad x201. Installation of Ubuntu 10.10 went smoothly and is running on current updates. The maschine runs the current Bios as well. Thanks to the thinkpad_acpi almost everything works fine. 

The fan is running quite a lot though. I went ahead to install thinkfan, but it complained about sensor values missing ... so I checked the values ... and got the following:

```

$ cat /proc/acpi/ibm/thermal 
temperatures:    42 0 0 0 0 0 0 0

```and

```

$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +43.0°C  (crit = +100.0°C)                  

thinkpad-isa-0000
Adapter: ISA adapter
fan1:       1978 RPM
temp1:       +43.0°C                                    
temp2:        +0.0°C                                    
temp3:        +0.0°C                                    
temp4:        +0.0°C                                    
temp5:        +0.0°C                                    
temp6:        +0.0°C                                    
temp7:        +0.0°C                                    
temp8:        +0.0°C  

```why do I only have one temperature reading ???

I have the following modules loaded:

```

$ lsmod 
Module                  Size  Used by
binfmt_misc             6599  1 
tp_smapi               20490  0 
thinkpad_ec             5554  1 tp_smapi
parport_pc             26378  0 
ppdev                   5556  0 
btusb                  11001  0 
bluetooth              50500  1 btusb
snd_hda_codec_intelhdmi     9812  1 
snd_hda_codec_conexant    29939  1 
joydev                  8735  0 
thinkpad_acpi          67659  0 
snd_hda_intel          22203  2 
arc4                    1165  2 
snd_hda_codec          87552  3 snd_hda_codec_intelhdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71603  2 snd_hda_intel,snd_hda_codec
i915                  293387  3 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
iwlagn                179815  0 
snd_seq_midi_event      6047  1 snd_seq_midi
drm_kms_helper         30200  1 i915
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
drm                   168726  4 i915,drm_kms_helper
qcserial                3484  0 
usb_wwan                9953  1 qcserial
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
usbserial              33100  2 qcserial,usb_wwan
iwlcore               127479  1 iwlagn
tpm_tis                 7658  0 
tpm                    13741  1 tpm_tis
uvcvideo               55911  0 
videodev               43098  1 uvcvideo
mac80211              231541  2 iwlagn,iwlcore
intel_agp              26784  2 i915
tpm_bios                5310  1 tpm
v4l1_compat            13359  2 uvcvideo,videodev
led_class               2633  1 thinkpad_acpi
nvram                   6342  1 thinkpad_acpi
i2c_algo_bit            5168  1 i915
cfg80211              144470  3 iwlagn,iwlcore,mac80211
psmouse                59033  0 
intel_ips              11101  0 
snd                    49006  14 snd_hda_codec_conexant,thinkpad_acpi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               4022  0 
agpgart                32075  2 drm,intel_agp
video                  18712  1 i915
output                  1883  1 video
soundcore                880  1 snd
snd_page_alloc          7216  2 snd_hda_intel,snd_pcm
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
ahci                   19013  0 
e1000e                133436  0 
libahci                21731  4 ahci

```anyone some thoughts on this ?

cheers, chik3n

---

### Post by mchmarny on 2011-01-26
have you ever figure this one out? I love my new X201 with a solid state drive and i7 processor but the fan speed is killing me. 

```

cat /proc/acpi/ibm/thermal
temperatures:	50 0 0 0 0 0 0 0

...

sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +50.0°C  (crit = +100.0°C)                  

thinkpad-isa-0000
Adapter: ISA adapter
fan1:       3573 RPM
temp1:       +50.0°C                                    
temp2:        +0.0°C                                    
temp3:        +0.0°C                                    
temp4:        +0.0°C                                    
temp5:        +0.0°C                                    
temp6:        +0.0°C                                    
temp7:        +0.0°C                                    
temp8:        +0.0°C  

```

---

### Post by chik3n on 2011-01-27
Hi,

I did not fiddle with any sensor values. Just installed thinkfan and left everything as it is. So far the max cpu temp was 62° while playing games. usually it's around 50°. And the thinkpad did not die on my once !!

Fan speed around 1900 - 0 rpm which is quite enough.

i7, solid state ... nice.

cheers, chik3n

---

### Post by mchmarny on 2011-02-19
I went with these settings and it is a lot better. 
[http://jaysherby.blogspot.com/2010/05/thinkfan-in-ubuntu-karmic.html]("http://jaysherby.blogspot.com/2010/05/thinkfan-in-ubuntu-karmic.html")

---

