---
title: "Frish Ubuntu 16.04 has Problem with Bluetooth BCM43142"
date: 2016-09-19
forum: Hardware
---

### Post by szer0p on 2016-09-19
Hello everyone,

I installed ubuntu 16.04 lts on my laptop HP-Compaq PAVILION 15-P209NG, its very slow when its start up takes 1 min. 

i pressed strg + alt + f1 to see what is going on: 

Bluetooth: hci0 command 0x1001 tx timeout
Bluetooth: hci0: BCM: Reading local version info failed (-110)
Bluetooth: hci0 command 0x1001 tx timeout
Bluetooth: hci0: BCM: Reading local version info failed (-110)

i tried so much things but nothing fixed the problem, another thing i think also the Wireless signal is week.

```

dmesg | grep Bluetooth
[   15.203713] Bluetooth: Core ver 2.21
[   15.203727] Bluetooth: HCI device and connection manager initialized
[   15.203729] Bluetooth: HCI socket layer initialized
[   15.203731] Bluetooth: L2CAP socket layer initialized
[   15.203738] Bluetooth: SCO socket layer initialized
[   17.975685] Bluetooth: hci0 command 0x1001 tx timeout
[   25.968209] Bluetooth: hci0: BCM: Reading local version info failed (-110)
[   27.972307] Bluetooth: hci0 command 0x1001 tx timeout
[   35.968825] Bluetooth: hci0: BCM: Reading local version info failed (-110)
[   37.116425] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   37.116428] Bluetooth: BNEP filters: protocol multicast
[   37.116431] Bluetooth: BNEP socket layer initialized

```

```

$ lspci | grep BCM
08:00.0 Network controller: Broadcom Corporation BCM43142 802.11b/g/n (rev 01)

```

```

$ lsmod
Module                  Size  Used by
nf_conntrack_ipv6      20480  1
nf_defrag_ipv6         36864  1 nf_conntrack_ipv6
xt_tcpudp              16384  14
nf_conntrack_ipv4      16384  1
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  2
nf_conntrack          106496  3 xt_conntrack,nf_conntrack_ipv4,nf_conntrack_ipv6
ip6table_filter        16384  1
ip6_tables             28672  1 ip6table_filter
iptable_filter         16384  1
ip_tables              24576  1 iptable_filter
x_tables               36864  6 ip6table_filter,ip_tables,xt_tcpudp,xt_conntrack,iptable_filter,ip6_tables
bnep                   20480  2
bbswitch               16384  0
nls_iso8859_1          16384  1
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
uvcvideo               90112  0
nvidia_uvm            745472  0
intel_rapl             20480  0
btintel                16384  1 btusb
bluetooth             520192  10 bnep,btbcm,btrtl,btusb,btintel
videobuf2_vmalloc      16384  1 uvcvideo
x86_pkg_temp_thermal    16384  0
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
intel_powerclamp       16384  0
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
coretemp               16384  0
v4l2_common            16384  1 videobuf2_v4l2
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
media                  24576  2 uvcvideo,videodev
snd_hda_codec_hdmi     53248  1
snd_hda_codec_realtek    86016  1
kvm                   540672  0
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
irqbypass              16384  1 kvm
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
snd_hda_intel          36864  5
wl                   6365184  0
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
rtsx_pci_ms            20480  0
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
snd_hwdep              16384  1 snd_hda_codec
memstick               20480  1 rtsx_pci_ms
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
aesni_intel           167936  0
aes_x86_64             20480  1 aesni_intel
snd_seq_midi           16384  0
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
hp_accel               28672  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
cryptd                 20480  2 aesni_intel,ablk_helper
snd_timer              32768  2 snd_pcm,snd_seq
cfg80211              565248  1 wl
snd                    81920  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              16384  1 snd
joydev                 20480  0
input_leds             16384  0
serio_raw              16384  0
lis3lv02d              20480  1 hp_accel
mei_me                 36864  0
input_polldev          16384  1 lis3lv02d
mei                    98304  1 mei_me
8250_fintek            16384  0
hp_wireless            16384  0
wmi                    20480  1 hp_wmi
acpi_pad               20480  0
shpchp                 36864  0
lpc_ich                24576  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
rtsx_pci_sdmmc         24576  0
psmouse               126976  0
i915                 1208320  3
nvidia_drm             53248  1
nvidia_modeset        778240  3 nvidia_drm
nvidia              11931648  54 nvidia_modeset,nvidia_uvm
ahci                   36864  3
i2c_algo_bit           16384  1 i915
libahci                32768  1 ahci
drm_kms_helper        147456  2 i915,nvidia_drm
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
r8169                  81920  0
drm                   364544  8 i915,drm_kms_helper,nvidia_drm
rtsx_pci               53248  2 rtsx_pci_ms,rtsx_pci_sdmmc
mii                    16384  1 r8169
fjes                   28672  0
video                  40960  1 i915

```

```

dpkg -l | egrep 'bluetooth|bluez'
ii  blueman                                       2.0.4-1ubuntu2                                              amd64        Graphical bluetooth manager
ii  bluez                                         5.37-0ubuntu5                                               amd64        Bluetooth tools and daemons
ii  bluez-cups                                    5.37-0ubuntu5                                               amd64        Bluetooth printer driver for CUPS
ii  bluez-obexd                                   5.37-0ubuntu5                                               amd64        bluez obex daemon
ii  gnome-bluetooth                               3.18.2-1ubuntu2                                             amd64        GNOME Bluetooth tools
ii  indicator-bluetooth                           0.0.6+16.04.20160526-0ubuntu1                               amd64        System bluetooth indicator.
ii  libbluetooth3:amd64                           5.37-0ubuntu5                                               amd64        Library to use the BlueZ Linux Bluetooth stack
ii  libgnome-bluetooth13:amd64                    3.18.2-1ubuntu2                                             amd64        GNOME Bluetooth tools - support library
ii  pulseaudio-module-bluetooth                   1:8.0-0ubuntu3                                              amd64        Bluetooth module for PulseAudio sound server

```

```

 rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```



that was all the records from my laptop, have anyone idea how could i fix this problem? 

thanks:)

---

