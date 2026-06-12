---
title: "SAA7160 ( TBS 6680 ) problems, module does not load, no dvb adaptor nodes created."
date: 2016-10-22
forum: Hardware
---

### Post by isprins on 2016-10-22
Hi, i have followed the instructions here:
[https://linuxtv.org/wiki/index.php/TBS_driver_installation#Building_the_Open_Source_Driver](https://linuxtv.org/wiki/index.php/TBS_driver_installation#Building_the_Open_Source_Driver)

My kernel is:
4.4.0-45-generic #66-Ubuntu SMP Wed Oct 19 14:12:37 UTC 2016 x86_64
x86_64 x86_64 GNU/Linux


The problem is that the module does not load on boot,at least it looks
like that.

There are nothing about saa7160 or similar in the dmesg output.

lspci -v results in:
03:00.0 Multimedia controller: Philips Semiconductors SAA7160 (rev 03)
    Subsystem: Device 6680:0001
    Flags: bus master, fast devsel, latency 0, IRQ 5
    Memory at f7400000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: [40] MSI: Enable- Count=1/32 Maskable- 64bit+
    Capabilities: [50] Express Endpoint, MSI 00
    Capabilities: [74] Power Management version 2
    Capabilities: [80] Vendor Specific Information: Len=50 <?>
    Capabilities: [100] Vendor Specific Information: ID=0000 Rev=0
Len=088 <?>


grep saa716x /etc/modprobe.d/*  results in:
/etc/modprobe.d/saa716x_budget.conf:options saa716x_budget int_type=1

lsmod results in:
Module                  Size  Used by
eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
input_leds             16384  0
joydev                 20480  0
snd_hda_codec_hdmi     53248  1
sparse_keymap          16384  1 asus_wmi
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
snd_hda_codec_realtek    86016  1
kvm                   540672  0
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_intel          40960  5
snd_hda_codec         135168  4
snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           73728  5
snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  4
snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
mei_me                 36864  0
ie31200_edac           16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
edac_core              53248  1 ie31200_edac
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  21
snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
mei                    98304  1 mei_me
aesni_intel           167936  0
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  2 aesni_intel,ablk_helper
serio_raw              16384  0
lpc_ich                24576  0
soundcore              16384  1 snd
binfmt_misc            20480  1
mac_hid                16384  0
shpchp                 36864  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
uas                    24576  0
usb_storage            69632  1 uas
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
nouveau              1495040  4
mxm_wmi                16384  1 nouveau
i2c_algo_bit           16384  1 nouveau
ttm                    94208  1 nouveau
drm_kms_helper        155648  1 nouveau
psmouse               126976  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
e1000e                237568  0
ahci                   36864  2
libahci                32768  1 ahci
drm                   364544  7 ttm,drm_kms_helper,nouveau
ptp                    20480  1 e1000e
pps_core               20480  1 ptp
wmi                    20480  3 mxm_wmi,nouveau,asus_wmi
fjes                   28672  0
video                  40960  2 nouveau,asus_wmi


I don't know what causes this problem, or perhaps the instructions are outdated?
I have the same problem on Mythbuntu, with the newest distro installed.
Can anyone help?

---

