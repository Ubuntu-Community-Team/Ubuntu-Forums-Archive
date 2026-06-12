---
title: "Usb audio has low range and sound is choppy"
date: 2020-08-27
forum: Hardware
---

### Post by kingpenguin on 2020-08-27
I have just made the switch to ubuntu 20.04 but my usb Hyper-x cloud stinger wireless is having some issues. When I was on windows I could almost go to the back of my house with my headset before I would start having issues, but under ubuntu I can be sitting at my desk next to my computer and the audio keeps going in and out. Some times I even have to bend my head down closer to my tower which is right below me. Nothing else has changed other than the os is now linux. Any information that you will need just let me know and I would be glad to run it.

[lsusb output]
Bus 001 Device 005: ID 0951:16da Kingston Technology HyperX Cloud Stinger Wireless

[lsmod output]
Module                  Size  Used by
ses                    20480  0
enclosure              16384  1 ses
scsi_transport_sas     36864  1 ses
uas                    28672  0
usb_storage            77824  2 uas
xt_CHECKSUM            16384  1
xt_MASQUERADE          20480  3
xt_conntrack           16384  1
ipt_REJECT             16384  2
nf_reject_ipv4         16384  1 ipt_REJECT
xt_tcpudp              20480  9
ip6table_mangle        16384  1
ip6table_nat           16384  1
iptable_mangle         16384  1
iptable_nat            16384  1
nf_nat                 40960  3 ip6table_nat,iptable_nat,xt_MASQUERADE
nf_conntrack          139264  3 xt_conntrack,nf_nat,xt_MASQUERADE
nf_defrag_ipv6         24576  1 nf_conntrack
nf_defrag_ipv4         16384  1 nf_conntrack
libcrc32c              16384  2 nf_conntrack,nf_nat
nf_tables             135168  0
nfnetlink              16384  1 nf_tables
ip6table_filter        16384  1
ip6_tables             32768  3 ip6table_filter,ip6table_nat,ip6table_mangle
iptable_filter         16384  1
bpfilter               32768  0
bridge                176128  0
stp                    16384  1 bridge
llc                    16384  2 bridge,stp
nls_iso8859_1          16384  1
snd_hda_codec_hdmi     61440  1
edac_mce_amd           32768  0
kvm_amd                98304  0
kvm                   663552  1 kvm_amd
nvidia_uvm            970752  0
nvidia_drm             49152  10
nvidia_modeset       1114112  28 nvidia_drm
nvidia              20680704  1688 nvidia_uvm,nvidia_modeset
snd_hda_codec_realtek   122880  1
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_intel          53248  6
snd_usb_audio         262144  3
snd_intel_dspcfg       24576  1 snd_hda_intel
snd_hda_codec         131072  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_usbmidi_lib        36864  1 snd_usb_audio
snd_hda_core           90112  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
mc                     53248  1 snd_usb_audio
snd_hwdep              20480  2 snd_usb_audio,snd_hda_codec
snd_pcm               106496  6 snd_hda_codec_hdmi,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_hda_core
crct10dif_pclmul       16384  1
ghash_clmulni_intel    16384  0
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            36864  2 snd_seq_midi,snd_usbmidi_lib
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
aesni_intel           372736  0
snd_timer              36864  2 snd_seq,snd_pcm
crypto_simd            16384  1 aesni_intel
cryptd                 24576  2 crypto_simd,ghash_clmulni_intel
glue_helper            16384  1 aesni_intel
joydev                 24576  0
input_leds             16384  0
wmi_bmof               16384  0
drm_kms_helper        184320  1 nvidia_drm
snd                    90112  30 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
ipmi_devintf           20480  0
k10temp                16384  0
ipmi_msghandler       106496  2 ipmi_devintf,nvidia
fb_sys_fops            16384  1 drm_kms_helper
syscopyarea            16384  1 drm_kms_helper
ccp                    86016  1 kvm_amd
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
soundcore              16384  1 snd
mac_hid                16384  0
sch_fq_codel           20480  4
parport_pc             40960  1
ppdev                  24576  0
lp                     20480  0
drm                   491520  13 drm_kms_helper,nvidia_drm
parport                53248  3 parport_pc,lp,ppdev
ip_tables              32768  3 iptable_filter,iptable_nat,iptable_mangle
x_tables               40960  11 ip6table_filter,xt_conntrack,iptable_filter,xt_tcpudp,xt_CHECKSUM,ip6_tables,ipt_REJECT,ip_tables,ip6table_mangle,xt_MASQUERADE,iptable_mangle
autofs4                45056  2
hid_generic            16384  0
usbhid                 57344  0
hid                   131072  2 usbhid,hid_generic
crc32_pclmul           16384  0
i2c_piix4              28672  0
r8169                  90112  0
nvme                   49152  2
ahci                   40960  2
realtek                24576  1
libahci                32768  1 ahci
nvme_core             102400  4 nvme
wmi                    32768  1 wmi_bmof
gpio_amdpt             20480  0
gpio_generic           20480  1 gpio_amdpt

---

### Post by kingpenguin on 2020-08-27
I would have never though that this would matter but I figured out it had something to do with my usb transfer happening at the same time.

---

