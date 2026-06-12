---
title: "thinkpad_acpi: Invalid argument in quantal"
date: 2012-11-21
forum: Hardware
---

### Post by proteusvacuum on 2012-11-21
Hi,

I am trying to get thinkfan working in ubuntu 12.10 (64-bit) on a thinkpad x120e. When trying to load thinkpad_acpi with ```
modprobe thinkpad_acpi
```
I get the following error: 
```
FATAL: Error inserting thinkpad_acpi (/lib/modules/3.5.0-17-generic/kernel/drivers/platform/x86/thinkpad_acpi.ko): Invalid argument
```

I have not been able to find this anywhere online... anyone have any suggestions? I also tried loading coretemp to no avail.

Thanks!

---

### Post by 2F4U on 2012-11-21
Am I right in assuming that you did 

**sudo** modprobe thinkpad_acpi?

Can you post the output of lsmod?

---

### Post by proteusvacuum on 2012-11-23
Sorry, yes I should have specified that I did sudo.

here's my lsmod:

```
Module                  Size  Used by
nls_iso8859_1          12713  0 
rfcomm                 46619  0 
bnep                   18140  2 
bluetooth             209199  10 rfcomm,bnep
parport_pc             32688  0 
ppdev                  17073  0 
binfmt_misc            17500  1 
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12860  1 uvcvideo
videobuf2_memops       13368  1 videobuf2_vmalloc
snd_hda_codec_conexant    57842  1 
arc4                   12529  2 
snd_hda_codec_hdmi     32007  1 
snd_hda_intel          33491  5 
snd_hda_codec         134212  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
joydev                 17457  0 
iwlwifi               386826  0 
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
radeon                895653  3 
kvm_amd                55604  0 
snd_seq_midi           13324  0 
kvm                   414070  1 kvm_amd
snd_rawmidi            30512  1 snd_seq_midi
mac80211              539908  1 iwlwifi
snd_seq_midi_event     14899  1 snd_seq_midi
microcode              22803  0 
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
ttm                    83595  1 radeon
snd_timer              29425  2 snd_pcm,snd_seq
psmouse                95552  0 
drm_kms_helper         46784  1 radeon
serio_raw              13215  0 
cfg80211              206566  2 iwlwifi,mac80211
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   275528  5 radeon,ttm,drm_kms_helper
sp5100_tco             13697  0 
nvram                  14362  0 
k10temp                13126  0 
snd                    78734  20 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13205  0 
i2c_piix4              13167  0 
i2c_algo_bit           13413  1 radeon
video                  19335  0 
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
wmi                    19070  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
ums_realtek            17949  0 
uas                    17844  0 
r8169                  61650  0 
usb_storage            48838  1 ums_realtek

```

Thanks!

---

### Post by steeldriver on 2012-11-23
Hmm... since it's complaining about an invalid argument but you aren't actually supplying any parameters on the command line I wonder if it's reading something bad from a conf file in /etc/modprobe.d? Do you get any hits if you

```
grep -R thinkpad_acpi /etc/modprobe.d/
```I'm just thinking out loud here really - I don't really know anything about kernel modules OR acpi

---

### Post by proteusvacuum on 2012-11-23
Aha! your last post led me to an error.
In /etc/modprobe.d/thinkfan.conf I had inserted the line
```
options thinkpad_acpi fan_control=1
```
following some how-to somewhere.

Adding the extra parameter "experimental=1" fixed it.

so... my /etc/modprobe.d/thinkfan.conf now reads
```
options thinkpad_acpi experimental=1 fan_control=1
```

Loading the module now works, and thinkfan also works. 

Thanks for your help everyone!

---

