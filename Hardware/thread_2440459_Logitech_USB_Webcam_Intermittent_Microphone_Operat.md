---
title: "Logitech USB Webcam Intermittent Microphone Operation"
date: 2020-04-10
forum: Hardware
---

### Post by coop999 on 2020-04-10
Logitech HD Pro Webcam C920 is attached to USB port.   The camera works fine in all applications (e.g.  Cheese, GUVCView, Zoom, etc...).  However the built in microphone WILL NOT work.   I have confirmed in ALSAmixer the volume is up and not muted.   I have selected in pulseaudio the C920 microphonoe.    There is no registered input on the Input Level monitor in sound settings (Input Tab).   I have confirmed the kernel has loaded (using lsmod) the snd_usb_audio driver.  (output attached).   A look at the USB bus gives the output attached showing the webcam is attached and recognized.    I also have installed Pulse Audio Volumen Controls and PulseEffects.   

This is the "strange" thing.   I have a second Logitech C920 Camera.   If I plug that camera into another USB port while the first one is still attached, SOMETIMES,  the second camera's microphone will become a live mic input that can be used.   This doesn't always work but sporatically.   I have switched cameras so I have confirmed 100% that both cameras mics and camera function are at 100% operational.   There is something about recognizing the microphone USB driver that I can't seem to get working.    I have trolled dozens of forum articles and postings but none of them address this issue.     I do not have chipmonk audio, but no audio at all.    Any help or leads greatly appreciated.    Thank you, 
[B]
April 14:  Additional Details: [COLOR=#000000]Additional Information to original post. I subsequentially plugged a Logitech Pro 9000 USB camera/mic into the same setup and this works flawlessly both camera and microphone everytime plugged in. Even a "hot" plug in and no reboot. The Logitech 920 camera again is fully recognized and the microphone ("Stereo") is recognized as Left / Right input in Pulse Audio and in ALSA mixer (as a single mono input), but never produces any sound. This is only speculation but it appears the stereo sound / sound driver portion of the driver is not fully supported in the Logitech C920. Any new developments or "fixes" would be greatly appreciated. The current posts do not seem to address the issue. I probably looked at all of them as far back as 2001.[/COLOR][/B]


lsusb
Bus 002 Device 003: ID 058f:6364 Alcor Micro Corp. AU6477 Card Reader Controller
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 003: ID 046d:082d Logitech, Inc. HD Pro Webcam C920
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



lsmod Output: 
Module                  Size  Used by
xt_tcpudp              20480  3
snd_seq_dummy          16384  0
rfcomm                 81920  16
ip6table_filter        16384  1
ip6_tables             32768  1 ip6table_filter
iptable_filter         16384  1
bpfilter               24576  0
cmac                   16384  1
bnep                   24576  2
nvidia_uvm            929792  0
intel_rapl_msr         20480  0
uvcvideo               94208  2
snd_usb_audio         241664  3
videobuf2_vmalloc      20480  1 uvcvideo
videobuf2_memops       20480  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
snd_usbmidi_lib        36864  1 snd_usb_audio
videobuf2_common       49152  2 videobuf2_v4l2,uvcvideo
videodev              208896  5 videobuf2_v4l2,uvcvideo,videobuf2_common
mc                     53248  5 videodev,snd_usb_audio,videobuf2_v4l2,uvcvideo,videobuf2_common
joydev                 28672  0
input_leds             16384  0
nvidia_drm             49152  7
intel_rapl_common      24576  1 intel_rapl_msr
snd_hda_codec_realtek   118784  1
snd_hda_codec_hdmi     57344  1
nvidia_modeset       1114112  11 nvidia_drm
x86_pkg_temp_thermal    20480  0
intel_powerclamp       20480  0
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
coretemp               20480  0
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_hda_codec_realtek
nvidia              20402176  604 nvidia_uvm,nvidia_modeset
snd_hda_intel          49152  10
ath9k                 151552  0
kvm_intel             241664  0
btusb                  57344  0
snd_hda_codec         131072  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           90112  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
ath9k_common           36864  1 ath9k
snd_hwdep              20480  2 snd_usb_audio,snd_hda_codec
btrtl                  20480  1 btusb
ath9k_hw              475136  2 ath9k_common,ath9k
snd_pcm               102400  6 snd_hda_codec_hdmi,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_hda_core
kvm                   651264  1 kvm_intel
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
irqbypass              16384  1 kvm
btbcm                  16384  1 btusb
ath                    36864  3 ath9k_common,ath9k,ath9k_hw
btintel                24576  1 btusb
crct10dif_pclmul       16384  1
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
bluetooth             573440  41 btrtl,btintel,btbcm,bnep,btusb,rfcomm
mac80211              843776  1 ath9k
drm_kms_helper        180224  1 nvidia_drm
snd_rawmidi            36864  2 snd_seq_midi,snd_usbmidi_lib
snd_seq                69632  3 snd_seq_midi,snd_seq_midi_event,snd_seq_dummy
aesni_intel           372736  2
drm                   483328  10 drm_kms_helper,nvidia_drm
cfg80211              704512  4 ath9k_common,ath9k,ath,mac80211
aes_x86_64             20480  1 aesni_intel
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
crypto_simd            16384  1 aesni_intel
cryptd                 24576  2 crypto_simd,ghash_clmulni_intel
glue_helper            16384  1 aesni_intel
ecdh_generic           16384  2 bluetooth
ecc                    32768  1 ecdh_generic
intel_cstate           20480  0
snd_timer              36864  2 snd_seq,snd_pcm
ipmi_devintf           20480  0
ipmi_msghandler       102400  2 ipmi_devintf,nvidia
snd                    86016  38 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
libarc4                16384  1 mac80211
intel_rapl_perf        20480  0
fb_sys_fops            16384  1 drm_kms_helper
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
soundcore              16384  1 snd
mxm_wmi                16384  0
mei_me                 40960  0
lpc_ich                24576  0
mei                   102400  1 mei_me
mac_hid                16384  0
sch_fq_codel           20480  3
parport_pc             36864  0
ppdev                  24576  0
lp                     20480  0
parport                53248  3 parport_pc,lp,ppdev
ip_tables              32768  1 iptable_filter
x_tables               40960  5 ip6table_filter,iptable_filter,xt_tcpudp,ip6_tables,ip_tables
autofs4                45056  2
system76_io            16384  0
system76_acpi          16384  0
hid_logitech_hidpp     40960  0
hid_logitech_dj        24576  0
hid_generic            16384  0
usbhid                 53248  1 hid_logitech_dj
uas                    24576  0
hid                   131072  4 usbhid,hid_generic,hid_logitech_dj,hid_logitech_hidpp
usb_storage            73728  1 uas
mpt3sas               245760  1
firewire_ohci          40960  0
ahci                   40960  0
e1000e                249856  0
firewire_core          65536  1 firewire_ohci
libahci                32768  1 ahci
raid_class             16384  1 mpt3sas
crc_itu_t              16384  1 firewire_core
scsi_transport_sas     40960  1 mpt3sas
wmi                    32768  1 mxm_wmi
</pre>


Running Ubuntu 18.04 LTS.  Updates are turned on.  5.3.0-7625-generic.

---

### Post by coop999 on 2020-04-14
Additional Information to original post.    I subsequentially plugged a Logitech Pro 9000 USB camera/mic into the same setup and this works flawlessly both camera and microphone everytime plugged in.   Even a "hot" plug in and no reboot.   The Logitech 920 camera again is fully recognized and the microphone ("Stereo") is recognized as Left / Right input in Pulse Audio and in ALSA mixer (as a single mono input), but never produces any sound.   This is only speculation but it appears the stereo sound / sound driver portion of the driver is not fully supported in the Logitech C920.   Any new developments or "fixes" would be greatly appreciated.   The current posts do not seem to address the issue.   I probably looked at all of them as far back as 2001.

---

