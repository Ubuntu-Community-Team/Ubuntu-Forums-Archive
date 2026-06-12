---
title: "wifi requires Enable/Disable/Enable after sleep?"
date: 2015-09-10
forum: Hardware
---

### Post by mike353 on 2015-09-10
Sometime after upgrading from 14.10 to 15.04 my wifi stopped automatically restarting on wake. I have to uncheck "Enable WiFi" and then check it again to get the connection back. I've tested at home and at friend's house so the issue is not my router. I have no idea which modules need to be reloaded or blacklisted. Might be easier just to automate the Enable/Disable Wifi than figure it out?

Laptop: System76 Kudu Professional (Clevo)

lspci says I have:
```
 04:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

```

This is not the original Wifi card so I am not asking System76 for help. (I have no use for bluetooth and the original card would not work with Mac OS X, so I swapped it out for BCM4322.)

lsmod:
```
lsmod
Module                  Size  Used by
isofs                  40960  0 
uas                    24576  0 
usb_storage            69632  1 uas
nls_utf8               16384  0 
btrfs                 954368  0 
xor                    24576  1 btrfs
raid6_pq               98304  1 btrfs
ufs                    77824  0 
qnx4                   16384  0 
hfsplus               106496  0 
hfs                    57344  0 
minix                  36864  0 
ntfs                  102400  0 
msdos                  20480  0 
jfs                   188416  0 
xfs                   929792  0 
libcrc32c              16384  1 xfs
cpuid                  16384  0 
zfs                  2240512  1 
zunicode              331776  1 zfs
zcommon                53248  1 zfs
znvpair                90112  2 zfs,zcommon
spl                    94208  3 zfs,zcommon,znvpair
zavl                   16384  1 zfs
nvram                  16384  0 
msr                    16384  0 
binfmt_misc            20480  1 
bnep                   20480  2 
bluetooth             491520  7 bnep
uvcvideo               90112  0 
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_core         49152  1 uvcvideo
v4l2_common            16384  1 videobuf2_core
videodev              159744  3 uvcvideo,v4l2_common,videobuf2_core
media                  24576  2 uvcvideo,videodev
snd_hda_codec_via      32768  1 
snd_hda_codec_generic    69632  1 snd_hda_codec_via
snd_hda_codec_hdmi     53248  1 
intel_rapl             20480  0 
iosf_mbi               16384  1 intel_rapl
x86_pkg_temp_thermal    16384  0 
intel_powerclamp       20480  0 
coretemp               16384  0 
kvm_intel             151552  0 
kvm                   483328  1 kvm_intel
crct10dif_pclmul       16384  0 
wl                   6369280  0 
crc32_pclmul           16384  0 
ghash_clmulni_intel    16384  0 
aesni_intel           172032  0 
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
joydev                 20480  0 
cfg80211              540672  1 wl
serio_raw              16384  0 
rtsx_pci_ms            20480  0 
memstick               20480  1 rtsx_pci_ms
mei_me                 20480  0 
lpc_ich                24576  0 
mei                    90112  1 mei_me
wmi                    20480  0 
tpm_infineon           20480  0 
snd_hda_intel          36864  5 
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         143360  5 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              20480  1 snd_hda_codec
i915                 1060864  4 
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
video                  20480  1 i915
drm_kms_helper        131072  1 i915
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
drm                   348160  5 i915,drm_kms_helper
snd                    90112  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              16384  2 snd,snd_hda_codec
ie31200_edac           16384  0 
i2c_algo_bit           16384  1 i915
shpchp                 40960  0 
edac_core              53248  1 ie31200_edac
mac_hid                16384  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
autofs4                40960  2 
hid_generic            16384  0 
usbhid                 53248  0 
hid                   110592  2 hid_generic,usbhid
rtsx_pci_sdmmc         24576  0 
psmouse               118784  0 
ahci                   36864  3 
r8169                  81920  0 
libahci                32768  1 ahci
mii                    16384  1 r8169
rtsx_pci               49152  2 rtsx_pci_ms,rtsx_pci_sdmmc
```

---

### Post by houstonbofh on 2015-09-10
This is a common problem with WiFi cards, and not just on Linux.  The system on resume does not actually restart the card.  Your work around is actually the best one.  Other then that, you can do some custom scripting to bounce the wireless on resume, but that is more effort then it would be worth to me, unless you just want to learn.

---

### Post by mike353 on 2015-09-11
Ok, what does toggling that little check mark next to "Enable Wifi" do? I wonder if I put something like ```
service network restart
```
in /etc/pm/sleep.d/XX_wifi_toggle ?

Not much in there now:
```

/etc/pm/sleep.d&#10219; ls
10_grub-common  10_unattended-upgrades-hibernate  novatel_3g_suspend

```
I don't understand why the scripts in /etc/pm/sleep.d begin with numbers.  Kludge to make them run in a certain order? What number XX should I name it? Probably won't hurt anything to let it run on sleep and wake, so no need to fiddle with if..fi.

---

