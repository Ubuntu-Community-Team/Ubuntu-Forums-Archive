---
title: "USB device (gamepad) not recognized"
date: 2011-05-30
forum: Hardware
---

### Post by tylerl06 on 2011-05-30
Hello,

I bought a x-kim gptl-00c gamepad and when I plug it in it is not recognized.  
The dmesg read out is

[ 2173.516017] usb 5-2: new low speed USB device using uhci_hcd and address 63
[ 2173.928012] usb 5-2: device not accepting address 63, error -71

it is not detected from lsusb

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 099a:7202 Zippy Technology Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

(zippy == my keyboard)
it works on my windows computer and the USB port works as well.

This is my lsmod

Module                  Size  Used by
binfmt_misc            13213  1 
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  1 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
i915                  450944  3 
snd_seq_midi           13132  0 
joydev                 17322  0 
snd_rawmidi            25269  1 snd_seq_midi
ppdev                  12849  0 
snd_seq_midi_event     14475  1 snd_seq_midi
drm_kms_helper         40745  1 i915
drm                   180037  4 i915,drm_kms_helper
usbhid                 41704  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
hid                    77084  1 usbhid
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  12 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             32111  1 
asus_atk0110           17664  0 
i2c_algo_bit           13184  1 i915
psmouse                73312  0 
video                  18951  1 i915
soundcore              12600  1 snd
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
atl1c                  36237  0 


Any help would be GREATLY GREATLY appreciated- this has been driving me crazy!

Thanks in advance

---

### Post by tylerl06 on 2011-05-31
Anyone have any ideas?  I'm really struggling with this...
Please?

---

### Post by tylerl06 on 2011-06-02
Please?  Anyone? I could really use the help...:confused:

---

