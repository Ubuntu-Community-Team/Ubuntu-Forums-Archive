---
title: "not resuming after suspend"
date: 2011-07-30
forum: Hardware
---

### Post by harun3d on 2011-07-30
My Ubuntu 10.4 does not resume after suspend (stand by).  I have to do a forced shut down.  

I tried:
```
sudo gedit /etc/default/acpi-support
``` go to POST_VIDEO=
 and set it POST_VIDEO=false

It did not solve the problem.  Then I tried:
```
sudo gedit /etc/pm/config.d/00sleep_module
```Add a line at the end of file &#8216;SUSPEND_MODULES=&#8221;xhci&#8221; (file was empty)

Still not solved
(Toshiba satellite)

---

### Post by Toz on 2011-07-30
Open a terminal window, run the following commands and post back the results:
```
uname -r
lspci -vnn
sudo dmidecode -s system-manufacturer
sudo dmidecode -s system-product-name
```
and the contents of the file:
**/var/log/pm-suspend.log**

---

### Post by harun3d on 2011-07-30
```
uname -r
``` gave 2.6.32-33-generic
```
lspci -vnn
``` gave
```

00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
    Subsystem: Toshiba America Info Systems Device [1179:ff64]
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)
    Subsystem: Toshiba America Info Systems Device [1179:ff64]
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at 92100000 (64-bit, non-prefetchable) [size=1M]
    Memory at 80000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 5110 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)
    Subsystem: Toshiba America Info Systems Device [1179:ff64]
    Flags: bus master, fast devsel, latency 0
    Memory at 92200000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
    Subsystem: Toshiba America Info Systems Device [1179:ff64]
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 50c0 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
    Subsystem: Toshiba America Info Systems Device [1179:ff64]
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 50a0 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03) (prog-if 20)
    Subsystem: Toshiba America Info Systems Device [1179:ff64]
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at 94304c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
    Subsystem: Toshiba America Info Systems Device [1179:ff64]
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at 94300000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00003000-00004fff
    Memory behind bridge: 93300000-942fffff
    Prefetchable memory behind bridge: 0000000090000000-00000000910fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=09, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 92300000-932fffff
    Prefetchable memory behind bridge: 0000000091100000-00000000920fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
    Subsystem: Toshiba America Info Systems Device [1179:ff64]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 5080 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
    Subsystem: Toshiba America Info Systems Device [1179:ff64]
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 5060 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
    Subsystem: Toshiba America Info Systems Device [1179:ff64]
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 5040 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03) (prog-if 20)
    Subsystem: Toshiba America Info Systems Device [1179:ff64]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at 94304800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
    Subsystem: Toshiba America Info Systems Device [1179:ff64]
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03) (prog-if 8a [Master SecP PriP])
    Subsystem: Toshiba America Info Systems Device [1179:ff64]
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 50e0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03) (prog-if 01)
    Subsystem: Toshiba America Info Systems Device [1179:ff64]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 27
    I/O ports at 50f8 [size=8]
    I/O ports at 511c [size=4]
    I/O ports at 50f0 [size=8]
    I/O ports at 5118 [size=4]
    I/O ports at 5020 [size=32]
    Memory at 94304000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
    Subsystem: Toshiba America Info Systems Device [1179:ff64]
    Flags: medium devsel, IRQ 11
    Memory at 94305000 (32-bit, non-prefetchable) [size=256]
    I/O ports at 5000 [size=32]
    Kernel modules: i2c-i801

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Toshiba America Info Systems Device [1179:ff64]
    Flags: bus master, fast devsel, latency 0, IRQ 26
    I/O ports at 3000 [size=256]
    Memory at 90010000 (64-bit, prefetchable) [size=4K]
    Memory at 90000000 (64-bit, prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

```
```
sudo dmidecode -s system-manufacturer
``` is TOSHIBA
```
sudo dmidecode -s system-product-name
``` is Satellite L350

The contents of the file:/var/log/pm-suspend.log:
```

Initial commandline parameters: 
Wed Jul 20 20:54:45 CEST 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux hc-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203376  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
snd_pcm_oss            35308  0 
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
snd_mixer_oss          13746  1 snd_pcm_oss
vgastate                8961  1 vga16fb
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
arc4                    1153  2 
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
rtl8187                50680  0 
joydev                  8740  0 
i915                  288611  3 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
drm_kms_helper         29329  1 i915
mac80211              205402  1 rtl8187
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
drm                   162377  4 i915,drm_kms_helper
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
led_class               2864  1 rtl8187
cfg80211              126144  2 rtl8187,mac80211
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            5028  1 i915
soundcore               6620  1 snd
eeprom_93cx6            1333  1 rtl8187
uvcvideo               57374  0 
video                  17375  1 i915
videodev               34361  1 uvcvideo
psmouse                63677  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
serio_raw               3978  0 
v4l1_compat            13251  2 uvcvideo,videodev
output                  1871  1 video
intel_agp              24375  2 i915
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169
             total       used       free     shared    buffers     cached
Mem:       2051944     396444    1655500          0      52828     195284
-/+ buffers/cache:     148332    1903612
Swap:      1447928          0    1447928
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Wed Jul 20 20:54:46 CEST 2011: performing suspend
Wed Jul 20 22:41:53 CEST 2011: Awake.
Wed Jul 20 22:41:53 CEST 2011: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend:success.
/usr/lib/pm-utils/sleep.d/99video resume suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:success.
/usr/lib/pm-utils/sleep.d/95led resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend:success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:success.
/etc/pm/sleep.d/10_grub-common resume suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend:success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend:success.
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:success.
Wed Jul 20 22:41:54 CEST 2011: Finished.
Initial commandline parameters: 
Thu Jul 21 00:15:25 CEST 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux hc-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203376  1 
snd_hda_intel          22069  4 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
snd_pcm_oss            35308  0 
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
snd_mixer_oss          13746  1 snd_pcm_oss
vgastate                8961  1 vga16fb
snd_pcm                70694  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
arc4                    1153  2 
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
rtl8187                50680  0 
joydev                  8740  0 
i915                  288611  3 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
drm_kms_helper         29329  1 i915
mac80211              205402  1 rtl8187
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
drm                   162377  4 i915,drm_kms_helper
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
led_class               2864  1 rtl8187
cfg80211              126144  2 rtl8187,mac80211
snd                    54244  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            5028  1 i915
soundcore               6620  1 snd
eeprom_93cx6            1333  1 rtl8187
uvcvideo               57374  0 
video                  17375  1 i915
videodev               34361  1 uvcvideo
psmouse                63677  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
serio_raw               3978  0 
v4l1_compat            13251  2 uvcvideo,videodev
output                  1871  1 video
intel_agp              24375  2 i915
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169
             total       used       free     shared    buffers     cached
Mem:       2051944    1459780     592164          0      56132    1061204
-/+ buffers/cache:     342444    1709500
Swap:      1447928          0    1447928
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Thu Jul 21 00:15:26 CEST 2011: performing suspend
Initial commandline parameters: 
Thu Jul 21 19:32:39 CEST 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux hc-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
usbhid                 36110  0 
hid                    67288  1 usbhid
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
snd_hda_codec_realtek   203376  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rtl8187                50680  0 
i915                  288611  3 
mac80211              205402  1 rtl8187
led_class               2864  1 rtl8187
uvcvideo               57374  0 
videodev               34361  1 uvcvideo
drm_kms_helper         29329  1 i915
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l1_compat            13251  2 uvcvideo,videodev
cfg80211              126144  2 rtl8187,mac80211
eeprom_93cx6            1333  1 rtl8187
psmouse                63677  0 
serio_raw               3978  0 
drm                   162377  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
intel_agp              24375  2 i915
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 drm,intel_agp
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169
             total       used       free     shared    buffers     cached
Mem:       2051944     689592    1362352          0      60356     330672
-/+ buffers/cache:     298564    1753380
Swap:      1447928          0    1447928
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Thu Jul 21 19:32:41 CEST 2011: performing suspend
Thu Jul 21 22:42:44 CEST 2011: Awake.
Thu Jul 21 22:42:44 CEST 2011: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend:success.
/usr/lib/pm-utils/sleep.d/99video resume suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:success.
/usr/lib/pm-utils/sleep.d/95led resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend:success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:success.
/etc/pm/sleep.d/10_grub-common resume suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend:success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend:success.
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:success.
Thu Jul 21 22:42:45 CEST 2011: Finished.
Initial commandline parameters: 
Fri Jul 22 00:08:57 CEST 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux hc-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
usbhid                 36110  0 
hid                    67288  1 usbhid
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
snd_hda_codec_realtek   203376  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rtl8187                50680  0 
i915                  288611  3 
mac80211              205402  1 rtl8187
led_class               2864  1 rtl8187
uvcvideo               57374  0 
videodev               34361  1 uvcvideo
drm_kms_helper         29329  1 i915
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l1_compat            13251  2 uvcvideo,videodev
cfg80211              126144  2 rtl8187,mac80211
eeprom_93cx6            1333  1 rtl8187
psmouse                63677  0 
serio_raw               3978  0 
drm                   162377  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
intel_agp              24375  2 i915
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 drm,intel_agp
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169
             total       used       free     shared    buffers     cached
Mem:       2051944     528120    1523824          0      64884     305864
-/+ buffers/cache:     157372    1894572
Swap:      1447928          0    1447928
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Fri Jul 22 00:08:58 CEST 2011: performing suspend
Initial commandline parameters: 
Fri Jul 22 00:34:35 CEST 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux hc-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
snd_hda_codec_realtek   203376  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
rtl8187                50680  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  288611  3 
mac80211              205402  1 rtl8187
led_class               2864  1 rtl8187
drm_kms_helper         29329  1 i915
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               57374  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
cfg80211              126144  2 rtl8187,mac80211
eeprom_93cx6            1333  1 rtl8187
psmouse                63677  0 
serio_raw               3978  0 
drm                   162377  4 i915,drm_kms_helper
intel_agp              24375  2 i915
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 drm,intel_agp
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169
             total       used       free     shared    buffers     cached
Mem:       2051944     401596    1650348          0      39836     235412
-/+ buffers/cache:     126348    1925596
Swap:      1447928          0    1447928
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Fri Jul 22 00:34:36 CEST 2011: performing suspend
Fri Jul 22 01:32:36 CEST 2011: Awake.
Fri Jul 22 01:32:36 CEST 2011: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend:success.
/usr/lib/pm-utils/sleep.d/99video resume suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:success.
/usr/lib/pm-utils/sleep.d/95led resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend:success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:success.
/etc/pm/sleep.d/10_grub-common resume suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend:success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend:success.
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:success.
Fri Jul 22 01:32:37 CEST 2011: Finished.
Initial commandline parameters: 
Fri Jul 22 13:23:02 CEST 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux hc-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
snd_hda_codec_realtek   203376  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rtl8187                50680  0 
mac80211              205402  1 rtl8187
led_class               2864  1 rtl8187
i915                  288611  3 
psmouse                63677  0 
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              126144  2 rtl8187,mac80211
eeprom_93cx6            1333  1 rtl8187
serio_raw               3978  0 
drm_kms_helper         29329  1 i915
intel_agp              24375  2 i915
lp                      7028  0 
uvcvideo               57374  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
drm                   162377  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
soundcore               6620  1 snd
output                  1871  1 video
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 intel_agp,drm
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
r8169                  34140  0 
mii                     4381  1 r8169
ahci                   32360  2 
             total       used       free     shared    buffers     cached
Mem:       2051944     452312    1599632          0      42432     266724
-/+ buffers/cache:     143156    1908788
Swap:      1447928          0    1447928
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/70QuteCom suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Fri Jul 22 13:23:04 CEST 2011: performing suspend
Fri Jul 22 18:22:39 CEST 2011: Awake.
Fri Jul 22 18:22:39 CEST 2011: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend:success.
/usr/lib/pm-utils/sleep.d/99video resume suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:success.
/usr/lib/pm-utils/sleep.d/95led resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend:success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend:success.
/usr/lib/pm-utils/sleep.d/70QuteCom resume suspend:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:success.
/etc/pm/sleep.d/10_grub-common resume suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend:success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend:success.
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:success.
Fri Jul 22 18:22:40 CEST 2011: Finished.
Initial commandline parameters: 
Fri Jul 22 20:36:18 CEST 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux hc-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
snd_hda_codec_realtek   203376  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rtl8187                50680  0 
mac80211              205402  1 rtl8187
led_class               2864  1 rtl8187
i915                  288611  3 
psmouse                63677  0 
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              126144  2 rtl8187,mac80211
eeprom_93cx6            1333  1 rtl8187
serio_raw               3978  0 
drm_kms_helper         29329  1 i915
intel_agp              24375  2 i915
lp                      7028  0 
uvcvideo               57374  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
drm                   162377  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
soundcore               6620  1 snd
output                  1871  1 video
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 intel_agp,drm
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
r8169                  34140  0 
mii                     4381  1 r8169
ahci                   32360  2 
             total       used       free     shared    buffers     cached
Mem:       2051944     499780    1552164          0      52652     293864
-/+ buffers/cache:     153264    1898680
Swap:      1447928          0    1447928
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/70QuteCom suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Fri Jul 22 20:36:19 CEST 2011: performing suspend
Initial commandline parameters: 
Mon Jul 25 17:31:20 CEST 2011: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:Linux hc-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203376  1 
joydev                  8740  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rtl8187                50680  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              205402  1 rtl8187
led_class               2864  1 rtl8187
uvcvideo               57374  0 
i915                  288611  3 
cfg80211              126144  2 rtl8187,mac80211
drm_kms_helper         29329  1 i915
videodev               34361  1 uvcvideo
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
eeprom_93cx6            1333  1 rtl8187
v4l1_compat            13251  2 uvcvideo,videodev
drm                   162377  4 i915,drm_kms_helper
intel_agp              24375  2 i915
psmouse                63677  0 
i2c_algo_bit            5028  1 i915
serio_raw               3978  0 
video                  17375  1 i915
soundcore               6620  1 snd
output                  1871  1 video
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169
             total       used       free     shared    buffers     cached
Mem:       2051944     666400    1385544          0      74656     420952
-/+ buffers/cache:     170792    1881152
Swap:      1447928          0    1447928
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/70QuteCom hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate:success.
/etc/pm/sleep.d/action_wpa hibernate hibernate:success.
Mon Jul 25 17:31:22 CEST 2011: performing hibernate
Tue Jul 26 00:29:21 CEST 2011: Awake.
Tue Jul 26 00:29:21 CEST 2011: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/70QuteCom thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:success.
/etc/pm/sleep.d/10_grub-common thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:success.
Tue Jul 26 00:29:24 CEST 2011: Finished.
Initial commandline parameters: 
Tue Jul 26 01:39:02 CEST 2011: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:Linux hc-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203376  1 
joydev                  8740  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rtl8187                50680  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              205402  1 rtl8187
led_class               2864  1 rtl8187
uvcvideo               57374  0 
i915                  288611  3 
cfg80211              126144  2 rtl8187,mac80211
drm_kms_helper         29329  1 i915
videodev               34361  1 uvcvideo
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
eeprom_93cx6            1333  1 rtl8187
v4l1_compat            13251  2 uvcvideo,videodev
drm                   162377  4 i915,drm_kms_helper
intel_agp              24375  2 i915
psmouse                63677  0 
i2c_algo_bit            5028  1 i915
serio_raw               3978  0 
video                  17375  1 i915
soundcore               6620  1 snd
output                  1871  1 video
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169
             total       used       free     shared    buffers     cached
Mem:       2051944     614416    1437528          0      69724     373048
-/+ buffers/cache:     171644    1880300
Swap:      1447928          0    1447928
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/70QuteCom hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate:success.
/etc/pm/sleep.d/action_wpa hibernate hibernate:success.
Tue Jul 26 01:39:03 CEST 2011: performing hibernate
Tue Jul 26 06:04:20 CEST 2011: Awake.
Tue Jul 26 06:04:20 CEST 2011: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/70QuteCom thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:success.
/etc/pm/sleep.d/10_grub-common thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:success.
Tue Jul 26 06:04:23 CEST 2011: Finished.
Initial commandline parameters: 
Tue Jul 26 14:24:08 CEST 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux hc-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203376  1 
joydev                  8740  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rtl8187                50680  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              205402  1 rtl8187
led_class               2864  1 rtl8187
uvcvideo               57374  0 
i915                  288611  3 
cfg80211              126144  2 rtl8187,mac80211
drm_kms_helper         29329  1 i915
videodev               34361  1 uvcvideo
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
eeprom_93cx6            1333  1 rtl8187
v4l1_compat            13251  2 uvcvideo,videodev
drm                   162377  4 i915,drm_kms_helper
intel_agp              24375  2 i915
psmouse                63677  0 
i2c_algo_bit            5028  1 i915
serio_raw               3978  0 
video                  17375  1 i915
soundcore               6620  1 snd
output                  1871  1 video
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169
             total       used       free     shared    buffers     cached
Mem:       2051944     614168    1437776          0      87888     344132
-/+ buffers/cache:     182148    1869796
Swap:      1447928          0    1447928
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/70QuteCom suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Tue Jul 26 14:24:09 CEST 2011: performing suspend
Tue Jul 26 14:26:41 CEST 2011: Awake.
Tue Jul 26 14:26:41 CEST 2011: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend:success.
/usr/lib/pm-utils/sleep.d/99video resume suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:success.
/usr/lib/pm-utils/sleep.d/95led resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend:success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend:success.
/usr/lib/pm-utils/sleep.d/70QuteCom resume suspend:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:success.
/etc/pm/sleep.d/10_grub-common resume suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend:success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend:success.
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:success.
Tue Jul 26 14:26:41 CEST 2011: Finished.
Initial commandline parameters: 
Tue Jul 26 14:55:31 CEST 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux hc-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203376  1 
joydev                  8740  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rtl8187                50680  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              205402  1 rtl8187
led_class               2864  1 rtl8187
uvcvideo               57374  0 
i915                  288611  3 
cfg80211              126144  2 rtl8187,mac80211
drm_kms_helper         29329  1 i915
videodev               34361  1 uvcvideo
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
eeprom_93cx6            1333  1 rtl8187
v4l1_compat            13251  2 uvcvideo,videodev
drm                   162377  4 i915,drm_kms_helper
intel_agp              24375  2 i915
psmouse                63677  0 
i2c_algo_bit            5028  1 i915
serio_raw               3978  0 
video                  17375  1 i915
soundcore               6620  1 snd
output                  1871  1 video
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169
             total       used       free     shared    buffers     cached
Mem:       2051944     819188    1232756          0      89024     414296
-/+ buffers/cache:     315868    1736076
Swap:      1447928          0    1447928
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/70QuteCom suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Tue Jul 26 14:55:32 CEST 2011: performing suspend
Initial commandline parameters: 
Tue Jul 26 22:42:18 CEST 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux hc-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
snd_hda_codec_realtek   203376  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rtl8187                50680  0 
i915                  288611  3 
mac80211              205402  1 rtl8187
led_class               2864  1 rtl8187
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               57374  0 
drm_kms_helper         29329  1 i915
cfg80211              126144  2 rtl8187,mac80211
eeprom_93cx6            1333  1 rtl8187
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
soundcore               6620  1 snd
psmouse                63677  0 
lp                      7028  0 
serio_raw               3978  0 
drm                   162377  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
intel_agp              24375  2 i915
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 drm,intel_agp
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
r8169                  34140  0 
mii                     4381  1 r8169
ahci                   32360  3 
             total       used       free     shared    buffers     cached
Mem:       2051944     981132    1070812          0      84936     472400
-/+ buffers/cache:     423796    1628148
Swap:      1447928          0    1447928
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/70QuteCom suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Tue Jul 26 22:42:19 CEST 2011: performing suspend
Tue Jul 26 22:56:15 CEST 2011: Awake.
Tue Jul 26 22:56:15 CEST 2011: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend:success.
/usr/lib/pm-utils/sleep.d/99video resume suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:success.
/usr/lib/pm-utils/sleep.d/95led resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend:success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend:success.
/usr/lib/pm-utils/sleep.d/70QuteCom resume suspend:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:success.
/etc/pm/sleep.d/10_grub-common resume suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend:success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend:success.
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:success.
Tue Jul 26 22:56:16 CEST 2011: Finished.
Initial commandline parameters: 
Wed Jul 27 01:26:50 CEST 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux hc-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
snd_hda_codec_realtek   203376  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rtl8187                50680  0 
i915                  288611  3 
mac80211              205402  1 rtl8187
led_class               2864  1 rtl8187
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               57374  0 
drm_kms_helper         29329  1 i915
cfg80211              126144  2 rtl8187,mac80211
eeprom_93cx6            1333  1 rtl8187
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
soundcore               6620  1 snd
psmouse                63677  0 
lp                      7028  0 
serio_raw               3978  0 
drm                   162377  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
intel_agp              24375  2 i915
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 drm,intel_agp
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
r8169                  34140  0 
mii                     4381  1 r8169
ahci                   32360  2 
             total       used       free     shared    buffers     cached
Mem:       2051944     880016    1171928          0      81868     466164
-/+ buffers/cache:     331984    1719960
Swap:      1447928          0    1447928
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/70QuteCom suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Wed Jul 27 01:26:50 CEST 2011: performing suspend
Initial commandline parameters: 
Wed Jul 27 06:45:29 CEST 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux hc-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
joydev                  8740  0 
snd_hda_codec_realtek   203376  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
ppdev                   5259  0 
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rtl8187                50680  0 
i915                  288611  3 
drm_kms_helper         29329  1 i915
mac80211              205402  1 rtl8187
led_class               2864  1 rtl8187
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   162377  4 i915,drm_kms_helper
cfg80211              126144  2 rtl8187,mac80211
eeprom_93cx6            1333  1 rtl8187
psmouse                63677  0 
serio_raw               3978  0 
uvcvideo               57374  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
intel_agp              24375  2 i915
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
agpgart                31724  2 drm,intel_agp
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169
             total       used       free     shared    buffers     cached
Mem:       2051944     905044    1146900          0     133884     467600
-/+ buffers/cache:     303560    1748384
Swap:      1447928          0    1447928
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/70QuteCom suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Wed Jul 27 06:45:31 CEST 2011: performing suspend
Wed Jul 27 11:07:47 CEST 2011: Awake.
Wed Jul 27 11:07:47 CEST 2011: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend:success.
/usr/lib/pm-utils/sleep.d/99video resume suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:success.
/usr/lib/pm-utils/sleep.d/95led resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend:success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend:success.
/usr/lib/pm-utils/sleep.d/70QuteCom resume suspend:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:success.
/etc/pm/sleep.d/10_grub-common resume suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend:success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend:success.
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:success.
Wed Jul 27 11:07:48 CEST 2011: Finished.
Initial commandline parameters: 
Wed Jul 27 11:16:57 CEST 2011: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:Linux hc-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
joydev                  8740  0 
snd_hda_codec_realtek   203376  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
ppdev                   5259  0 
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rtl8187                50680  0 
i915                  288611  3 
drm_kms_helper         29329  1 i915
mac80211              205402  1 rtl8187
led_class               2864  1 rtl8187
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   162377  4 i915,drm_kms_helper
cfg80211              126144  2 rtl8187,mac80211
eeprom_93cx6            1333  1 rtl8187
psmouse                63677  0 
serio_raw               3978  0 
uvcvideo               57374  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
intel_agp              24375  2 i915
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
agpgart                31724  2 drm,intel_agp
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169
             total       used       free     shared    buffers     cached
Mem:       2051944    1009432    1042512          0     133920     512836
-/+ buffers/cache:     362676    1689268
Swap:      1447928          0    1447928
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/70QuteCom hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate:success.
/etc/pm/sleep.d/action_wpa hibernate hibernate:success.
Wed Jul 27 11:16:57 CEST 2011: performing hibernate
Wed Jul 27 11:46:46 CEST 2011: Awake.
Wed Jul 27 11:46:46 CEST 2011: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/70QuteCom thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:success.
/etc/pm/sleep.d/10_grub-common thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:success.
Wed Jul 27 11:47:05 CEST 2011: Finished.
Initial commandline parameters: 
Wed Jul 27 16:45:23 CEST 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux hc-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
joydev                  8740  0 
snd_hda_codec_realtek   203376  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
ppdev                   5259  0 
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rtl8187                50680  0 
i915                  288611  3 
drm_kms_helper         29329  1 i915
mac80211              205402  1 rtl8187
led_class               2864  1 rtl8187
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   162377  4 i915,drm_kms_helper
cfg80211              126144  2 rtl8187,mac80211
eeprom_93cx6            1333  1 rtl8187
psmouse                63677  0 
serio_raw               3978  0 
uvcvideo               57374  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
intel_agp              24375  2 i915
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
agpgart                31724  2 drm,intel_agp
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169
             total       used       free     shared    buffers     cached
Mem:       2051944     443632    1608312          0      49232     224420
-/+ buffers/cache:     169980    1881964
Swap:      1447928      77276    1370652
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/70QuteCom suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Wed Jul 27 16:45:24 CEST 2011: performing suspend
Initial commandline parameters: 
Wed Jul 27 20:36:10 CEST 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux hc-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
snd_hda_codec_realtek   203376  1 
vgastate                8961  1 vga16fb
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
i915                  288611  3 
snd_seq_dummy           1338  0 
drm_kms_helper         29329  1 i915
snd_seq_oss            26722  0 
joydev                  8740  0 
drm                   162377  4 i915,drm_kms_helper
rtl8187                50680  0 
snd_seq_midi            4557  0 
uvcvideo               57374  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
i2c_algo_bit            5028  1 i915
videodev               34361  1 uvcvideo
mac80211              205402  1 rtl8187
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
video                  17375  1 i915
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
led_class               2864  1 rtl8187
v4l1_compat            13251  2 uvcvideo,videodev
soundcore               6620  1 snd
psmouse                63677  0 
cfg80211              126144  2 rtl8187,mac80211
output                  1871  1 video
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
intel_agp              24375  2 i915
eeprom_93cx6            1333  1 rtl8187
agpgart                31724  2 drm,intel_agp
serio_raw               3978  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
r8169                  34140  0 
mii                     4381  1 r8169
ahci                   32360  2 
             total       used       free     shared    buffers     cached
Mem:       2051944     862136    1189808          0     104984     397904
-/+ buffers/cache:     359248    1692696
Swap:      1447928          0    1447928
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/70QuteCom suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Wed Jul 27 20:36:11 CEST 2011: performing suspend
Wed Jul 27 23:03:50 CEST 2011: Awake.
Wed Jul 27 23:03:50 CEST 2011: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend:success.
/usr/lib/pm-utils/sleep.d/99video resume suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:success.
/usr/lib/pm-utils/sleep.d/95led resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend:success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend:success.
/usr/lib/pm-utils/sleep.d/70QuteCom resume suspend:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:success.
/etc/pm/sleep.d/10_grub-common resume suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend:success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend:success.
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:success.
Wed Jul 27 23:03:51 CEST 2011: Finished.
Initial commandline parameters: 
Wed Jul 27 23:04:13 CEST 2011: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:Linux hc-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
snd_hda_codec_realtek   203376  1 
vgastate                8961  1 vga16fb
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
i915                  288611  3 
snd_seq_dummy           1338  0 
drm_kms_helper         29329  1 i915
snd_seq_oss            26722  0 
joydev                  8740  0 
drm                   162377  4 i915,drm_kms_helper
rtl8187                50680  0 
snd_seq_midi            4557  0 
uvcvideo               57374  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
i2c_algo_bit            5028  1 i915
videodev               34361  1 uvcvideo
mac80211              205402  1 rtl8187
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
video                  17375  1 i915
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
led_class               2864  1 rtl8187
v4l1_compat            13251  2 uvcvideo,videodev
soundcore               6620  1 snd
psmouse                63677  0 
cfg80211              126144  2 rtl8187,mac80211
output                  1871  1 video
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
intel_agp              24375  2 i915
eeprom_93cx6            1333  1 rtl8187
agpgart                31724  2 drm,intel_agp
serio_raw               3978  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
r8169                  34140  0 
mii                     4381  1 r8169
ahci                   32360  2 
             total       used       free     shared    buffers     cached
Mem:       2051944     858760    1193184          0     105224     391780
-/+ buffers/cache:     361756    1690188
Swap:      1447928          0    1447928
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/70QuteCom hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate:success.
/etc/pm/sleep.d/action_wpa hibernate hibernate:success.
Wed Jul 27 23:04:14 CEST 2011: performing hibernate
Thu Jul 28 16:45:22 CEST 2011: Awake.
Thu Jul 28 16:45:22 CEST 2011: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/70QuteCom thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:success.
/etc/pm/sleep.d/10_grub-common thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:success.
Thu Jul 28 16:45:32 CEST 2011: Finished.
Initial commandline parameters: 
Fri Jul 29 01:29:35 CEST 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux hc-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
nls_iso8859_1           3249  0 
nls_cp437               4919  0 
vfat                    8933  0 
fat                    47767  1 vfat
usb_storage            39841  0 
binfmt_misc             6587  1 
ppdev                   5259  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
snd_hda_codec_realtek   203376  1 
vgastate                8961  1 vga16fb
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
i915                  288611  3 
snd_seq_dummy           1338  0 
drm_kms_helper         29329  1 i915
snd_seq_oss            26722  0 
joydev                  8740  0 
drm                   162377  4 i915,drm_kms_helper
rtl8187                50680  0 
snd_seq_midi            4557  0 
uvcvideo               57374  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
i2c_algo_bit            5028  1 i915
videodev               34361  1 uvcvideo
mac80211              205402  1 rtl8187
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
video                  17375  1 i915
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
led_class               2864  1 rtl8187
v4l1_compat            13251  2 uvcvideo,videodev
soundcore               6620  1 snd
psmouse                63677  0 
cfg80211              126144  2 rtl8187,mac80211
output                  1871  1 video
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
intel_agp              24375  2 i915
eeprom_93cx6            1333  1 rtl8187
agpgart                31724  2 drm,intel_agp
serio_raw               3978  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
r8169                  34140  0 
mii                     4381  1 r8169
ahci                   32360  2 
             total       used       free     shared    buffers     cached
Mem:       2051944     555100    1496844          0      42588     323076
-/+ buffers/cache:     189436    1862508
Swap:      1447928      63400    1384528
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/70QuteCom suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Fri Jul 29 01:29:37 CEST 2011: performing suspend
Initial commandline parameters: 
Fri Jul 29 03:41:57 CEST 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux hc-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
snd_hda_codec_realtek   203376  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
snd_hda_intel          22069  4 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i915                  288611  3 
drm_kms_helper         29329  1 i915
rtl8187                50680  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm                   162377  4 i915,drm_kms_helper
mac80211              205402  1 rtl8187
led_class               2864  1 rtl8187
uvcvideo               57374  0 
videodev               34361  1 uvcvideo
i2c_algo_bit            5028  1 i915
v4l1_compat            13251  2 uvcvideo,videodev
cfg80211              126144  2 rtl8187,mac80211
eeprom_93cx6            1333  1 rtl8187
psmouse                63677  0 
snd                    54244  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              24375  2 i915
serio_raw               3978  0 
agpgart                31724  2 drm,intel_agp
video                  17375  1 i915
output                  1871  1 video
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169
             total       used       free     shared    buffers     cached
Mem:       2051944     940012    1111932          0     102168     481384
-/+ buffers/cache:     356460    1695484
Swap:      1447928          0    1447928
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/70QuteCom suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Fri Jul 29 03:41:58 CEST 2011: performing suspend
Fri Jul 29 03:42:24 CEST 2011: Awake.
Fri Jul 29 03:42:24 CEST 2011: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend:success.
/usr/lib/pm-utils/sleep.d/99video resume suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:success.
/usr/lib/pm-utils/sleep.d/95led resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend:success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend:success.
/usr/lib/pm-utils/sleep.d/70QuteCom resume suspend:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:success.
/etc/pm/sleep.d/10_grub-common resume suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend:success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend:success.
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:success.
Fri Jul 29 03:42:25 CEST 2011: Finished.
Initial commandline parameters: 
Fri Jul 29 03:42:43 CEST 2011: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:Linux hc-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
snd_hda_codec_realtek   203376  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
snd_hda_intel          22069  4 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i915                  288611  3 
drm_kms_helper         29329  1 i915
rtl8187                50680  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm                   162377  4 i915,drm_kms_helper
mac80211              205402  1 rtl8187
led_class               2864  1 rtl8187
uvcvideo               57374  0 
videodev               34361  1 uvcvideo
i2c_algo_bit            5028  1 i915
v4l1_compat            13251  2 uvcvideo,videodev
cfg80211              126144  2 rtl8187,mac80211
eeprom_93cx6            1333  1 rtl8187
psmouse                63677  0 
snd                    54244  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              24375  2 i915
serio_raw               3978  0 
agpgart                31724  2 drm,intel_agp
video                  17375  1 i915
output                  1871  1 video
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169
             total       used       free     shared    buffers     cached
Mem:       2051944     931328    1120616          0     102296     475096
-/+ buffers/cache:     353936    1698008
Swap:      1447928          0    1447928
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/70QuteCom hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate:success.
/etc/pm/sleep.d/action_wpa hibernate hibernate:success.
Fri Jul 29 03:42:44 CEST 2011: performing hibernate
Fri Jul 29 04:06:43 CEST 2011: Awake.
Fri Jul 29 04:06:43 CEST 2011: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/70QuteCom thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:success.
/etc/pm/sleep.d/10_grub-common thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:success.
Fri Jul 29 04:07:22 CEST 2011: Finished.
Initial commandline parameters: 
Fri Jul 29 07:36:46 CEST 2011: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:Linux hc-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
snd_hda_codec_realtek   203376  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i915                  288611  3 
drm_kms_helper         29329  1 i915
rtl8187                50680  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm                   162377  4 i915,drm_kms_helper
mac80211              205402  1 rtl8187
led_class               2864  1 rtl8187
uvcvideo               57374  0 
videodev               34361  1 uvcvideo
i2c_algo_bit            5028  1 i915
v4l1_compat            13251  2 uvcvideo,videodev
cfg80211              126144  2 rtl8187,mac80211
eeprom_93cx6            1333  1 rtl8187
psmouse                63677  0 
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              24375  2 i915
serio_raw               3978  0 
agpgart                31724  2 drm,intel_agp
video                  17375  1 i915
output                  1871  1 video
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169
             total       used       free     shared    buffers     cached
Mem:       2051944     350512    1701432          0      31080     191544
-/+ buffers/cache:     127888    1924056
Swap:      1447928      70252    1377676
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/70QuteCom hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate:success.
/etc/pm/sleep.d/action_wpa hibernate hibernate:success.
Fri Jul 29 07:36:47 CEST 2011: performing hibernate
Fri Jul 29 13:10:11 CEST 2011: Awake.
Fri Jul 29 13:10:11 CEST 2011: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/70QuteCom thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:success.
/etc/pm/sleep.d/10_grub-common thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:success.
Fri Jul 29 13:10:12 CEST 2011: Finished.
Initial commandline parameters: 
Fri Jul 29 13:32:36 CEST 2011: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:Linux hc-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
snd_hda_codec_realtek   203376  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i915                  288611  3 
drm_kms_helper         29329  1 i915
rtl8187                50680  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm                   162377  4 i915,drm_kms_helper
mac80211              205402  1 rtl8187
led_class               2864  1 rtl8187
uvcvideo               57374  0 
videodev               34361  1 uvcvideo
i2c_algo_bit            5028  1 i915
v4l1_compat            13251  2 uvcvideo,videodev
cfg80211              126144  2 rtl8187,mac80211
eeprom_93cx6            1333  1 rtl8187
psmouse                63677  0 
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              24375  2 i915
serio_raw               3978  0 
agpgart                31724  2 drm,intel_agp
video                  17375  1 i915
output                  1871  1 video
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169
             total       used       free     shared    buffers     cached
Mem:       2051944     372344    1679600          0      33680     203956
-/+ buffers/cache:     134708    1917236
Swap:      1447928      69108    1378820
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/70QuteCom hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate:success.
/etc/pm/sleep.d/action_wpa hibernate hibernate:success.
Fri Jul 29 13:32:37 CEST 2011: performing hibernate
Fri Jul 29 15:06:13 CEST 2011: Awake.
Fri Jul 29 15:06:13 CEST 2011: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/70QuteCom thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:success.
/etc/pm/sleep.d/10_grub-common thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:success.
Fri Jul 29 15:06:14 CEST 2011: Finished.
Initial commandline parameters: 
Sat Jul 30 00:54:02 CEST 2011: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:Linux hc-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
snd_hda_codec_realtek   203376  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i915                  288611  3 
drm_kms_helper         29329  1 i915
rtl8187                50680  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm                   162377  4 i915,drm_kms_helper
mac80211              205402  1 rtl8187
led_class               2864  1 rtl8187
uvcvideo               57374  0 
videodev               34361  1 uvcvideo
i2c_algo_bit            5028  1 i915
v4l1_compat            13251  2 uvcvideo,videodev
cfg80211              126144  2 rtl8187,mac80211
eeprom_93cx6            1333  1 rtl8187
psmouse                63677  0 
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              24375  2 i915
serio_raw               3978  0 
agpgart                31724  2 drm,intel_agp
video                  17375  1 i915
output                  1871  1 video
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169
             total       used       free     shared    buffers     cached
Mem:       2051944     471144    1580800          0      71300     243024
-/+ buffers/cache:     156820    1895124
Swap:      1447928      67540    1380388
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/70QuteCom hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate:success.
/etc/pm/sleep.d/action_wpa hibernate hibernate:success.
Sat Jul 30 00:54:03 CEST 2011: performing hibernate
Sat Jul 30 11:07:20 CEST 2011: Awake.
Sat Jul 30 11:07:20 CEST 2011: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/70QuteCom thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:success.
/etc/pm/sleep.d/10_grub-common thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:success.
Sat Jul 30 11:07:21 CEST 2011: Finished.
Initial commandline parameters: 
Sat Jul 30 13:09:59 CEST 2011: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:Linux hc-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
snd_hda_codec_realtek   203376  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i915                  288611  3 
drm_kms_helper         29329  1 i915
rtl8187                50680  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm                   162377  4 i915,drm_kms_helper
mac80211              205402  1 rtl8187
led_class               2864  1 rtl8187
uvcvideo               57374  0 
videodev               34361  1 uvcvideo
i2c_algo_bit            5028  1 i915
v4l1_compat            13251  2 uvcvideo,videodev
cfg80211              126144  2 rtl8187,mac80211
eeprom_93cx6            1333  1 rtl8187
psmouse                63677  0 
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              24375  2 i915
serio_raw               3978  0 
agpgart                31724  2 drm,intel_agp
video                  17375  1 i915
output                  1871  1 video
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169
             total       used       free     shared    buffers     cached
Mem:       2051944     569724    1482220          0     112124     286536
-/+ buffers/cache:     171064    1880880
Swap:      1447928      67340    1380588
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/70QuteCom hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate:success.
/etc/pm/sleep.d/action_wpa hibernate hibernate:success.
Sat Jul 30 13:10:00 CEST 2011: performing hibernate
Sat Jul 30 14:25:42 CEST 2011: Awake.
Sat Jul 30 14:25:42 CEST 2011: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/70QuteCom thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:success.
/etc/pm/sleep.d/10_grub-common thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:success.
Sat Jul 30 14:25:46 CEST 2011: Finished.
Initial commandline parameters: 
Sat Jul 30 18:24:29 CEST 2011: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:Linux hc-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
snd_hda_codec_realtek   203376  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i915                  288611  3 
drm_kms_helper         29329  1 i915
rtl8187                50680  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm                   162377  4 i915,drm_kms_helper
mac80211              205402  1 rtl8187
led_class               2864  1 rtl8187
uvcvideo               57374  0 
videodev               34361  1 uvcvideo
i2c_algo_bit            5028  1 i915
v4l1_compat            13251  2 uvcvideo,videodev
cfg80211              126144  2 rtl8187,mac80211
eeprom_93cx6            1333  1 rtl8187
psmouse                63677  0 
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              24375  2 i915
serio_raw               3978  0 
agpgart                31724  2 drm,intel_agp
video                  17375  1 i915
output                  1871  1 video
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169
             total       used       free     shared    buffers     cached
Mem:       2051944     792084    1259860          0     102688     346464
-/+ buffers/cache:     342932    1709012
Swap:      1447928      67052    1380876
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/70QuteCom hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate:success.
/etc/pm/sleep.d/action_wpa hibernate hibernate:success.
Sat Jul 30 18:24:30 CEST 2011: performing hibernate
Sat Jul 30 20:07:15 CEST 2011: Awake.
Sat Jul 30 20:07:15 CEST 2011: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/70QuteCom thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:success.
/etc/pm/sleep.d/10_grub-common thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:success.
Sat Jul 30 20:07:20 CEST 2011: Finished.
Initial commandline parameters: 
Sat Jul 30 20:21:42 CEST 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux hc-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
snd_hda_codec_realtek   203376  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i915                  288611  3 
drm_kms_helper         29329  1 i915
rtl8187                50680  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm                   162377  4 i915,drm_kms_helper
mac80211              205402  1 rtl8187
led_class               2864  1 rtl8187
uvcvideo               57374  0 
videodev               34361  1 uvcvideo
i2c_algo_bit            5028  1 i915
v4l1_compat            13251  2 uvcvideo,videodev
cfg80211              126144  2 rtl8187,mac80211
eeprom_93cx6            1333  1 rtl8187
psmouse                63677  0 
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              24375  2 i915
serio_raw               3978  0 
agpgart                31724  2 drm,intel_agp
video                  17375  1 i915
output                  1871  1 video
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169
             total       used       free     shared    buffers     cached
Mem:       2051944     574684    1477260          0      22440     224656
-/+ buffers/cache:     327588    1724356
Swap:      1447928      68452    1379476
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/70QuteCom suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:success.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Sat Jul 30 20:21:43 CEST 2011: performing suspend
Initial commandline parameters: 
Sat Jul 30 20:47:22 CEST 2011: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:Linux hc-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
snd_hda_codec_realtek   203376  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rtl8187                50680  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              205402  1 rtl8187
led_class               2864  1 rtl8187
i915                  288611  3 
uvcvideo               57374  0 
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63677  0 
drm_kms_helper         29329  1 i915
intel_agp              24375  2 i915
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
cfg80211              126144  2 rtl8187,mac80211
eeprom_93cx6            1333  1 rtl8187
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
drm                   162377  4 i915,drm_kms_helper
agpgart                31724  2 intel_agp,drm
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169
             total       used       free     shared    buffers     cached
Mem:       2051944     696800    1355144          0     104060     273020
-/+ buffers/cache:     319720    1732224
Swap:      1447928          0    1447928
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/70QuteCom hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate:success.
/etc/pm/sleep.d/action_wpa hibernate hibernate:success.
Sat Jul 30 20:47:23 CEST 2011: performing hibernate
Sun Jul 31 02:11:48 CEST 2011: Awake.
Sun Jul 31 02:11:48 CEST 2011: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/70QuteCom thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:success.
/etc/pm/sleep.d/10_grub-common thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:success.
Sun Jul 31 02:11:54 CEST 2011: Finished.

```

---

### Post by Toz on 2011-07-30
Let's try some kernel parameters first. See this link ([https://help.ubuntu.com/community/Grub2#Editing the GRUB 2 Menu During Boot]("https://help.ubuntu.com/community/Grub2#Editing the GRUB 2 Menu During Boot")) for instructions on how to test the kernel parameters. Try these:

```
acpi_osi=Linux
acpi_osi=\"Linux\"
```

If the suspend doesn't work, on reboot, post back the contents of **/var/log/dmesg.0**

---

### Post by harun3d on 2011-07-31
I have opened GNUB kernel menu by pressing e at the menu of operating systems.  I have added

```
acpi_osi=Linux  
acpi_osi=\"Linux\"
```at the end of the kernel menu (both lines at the same time)

I pressed Ctrl+x to boot.  I tested the suspend mode.  The first time the system resumed without problem.  The second time resuming did not work.  Like always: the on/off led of the laptop shows that the computer has already resumed but the screen is not even switched on.  Again I have done a forced shut down. 

contents of   /var/log/dmesg.0:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-33-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 (Ubuntu 2.6.32-33.70-generic 2.6.32.41+drm33.18)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f4de000 (usable)
[    0.000000]  BIOS-e820: 000000007f4de000 - 000000007f4e9000 (reserved)
[    0.000000]  BIOS-e820: 000000007f4e9000 - 000000007f543000 (usable)
[    0.000000]  BIOS-e820: 000000007f543000 - 000000007f546000 (reserved)
[    0.000000]  BIOS-e820: 000000007f546000 - 000000007f5bb000 (usable)
[    0.000000]  BIOS-e820: 000000007f5bb000 - 000000007f5bf000 (reserved)
[    0.000000]  BIOS-e820: 000000007f5bf000 - 000000007f66a000 (usable)
[    0.000000]  BIOS-e820: 000000007f66a000 - 000000007f6bf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f6bf000 - 000000007f700000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f700000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x7f66a max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFFE0000 mask FFFFE0000 write-protect
[    0.000000]   1 base 000000000 mask FC0000000 write-back
[    0.000000]   2 base 040000000 mask FC0000000 write-back
[    0.000000]   3 base 07F800000 mask FFF800000 uncachable
[    0.000000]   4 base 07F700000 mask FFFF00000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007f4de000 (usable)
[    0.000000]  modified: 000000007f4de000 - 000000007f4e9000 (reserved)
[    0.000000]  modified: 000000007f4e9000 - 000000007f543000 (usable)
[    0.000000]  modified: 000000007f543000 - 000000007f546000 (reserved)
[    0.000000]  modified: 000000007f546000 - 000000007f5bb000 (usable)
[    0.000000]  modified: 000000007f5bb000 - 000000007f5bf000 (reserved)
[    0.000000]  modified: 000000007f5bf000 - 000000007f66a000 (usable)
[    0.000000]  modified: 000000007f66a000 - 000000007f6bf000 (ACPI NVS)
[    0.000000]  modified: 000000007f6bf000 - 000000007f700000 (ACPI data)
[    0.000000]  modified: 000000007f700000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 3784f000 - 37fefdde
[    0.000000] Allocated new RAMDISK: 008e5000 - 01085dde
[    0.000000] Move RAMDISK from 000000003784f000 - 0000000037fefddd to 008e5000 - 01085ddd
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 TOSINV)
[    0.000000] ACPI: XSDT 7f6fe120 00064 (v01 TOSINV TOSINV00 00000001      01000013)
[    0.000000] ACPI: FACP 7f6fd000 000F4 (v04 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: DSDT 7f6f5000 07A3C (v01 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: FACS 7f675000 00040
[    0.000000] ACPI: APIC 7f6f4000 00068 (v02 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: HPET 7f6f3000 00038 (v01 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 7f6f2000 0003C (v01 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: ASF! 7f6f1000 000A5 (v32 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC 7f6f0000 00176 (v01 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: BOOT 7f6ef000 00028 (v01 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 7f6ee000 004C4 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008e0ef8]    TEXT DATA BSS ==> [0000100000 - 00008e0ef8]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008e1000 - 00008e415c]              BRK ==> [00008e1000 - 00008e415c]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008e5000 - 0001085dde]      NEW RAMDISK ==> [00008e5000 - 0001085dde]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00fe230] fe230
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007f66a
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007f4de
[    0.000000]     0: 0x0007f4e9 -> 0x0007f543
[    0.000000]     0: 0x0007f546 -> 0x0007f5bb
[    0.000000]     0: 0x0007f5bf -> 0x0007f66a
[    0.000000] On node 0 totalpages: 521715
[    0.000000] free_area_init_node: node 0, pgdat c079a7c0, node_mem_map c1087000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2301 pages used for memmap
[    0.000000]   HighMem zone: 292189 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:78000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36312 r0 d21032 u2097152
[    0.000000] pcpu-alloc: s36312 r0 d21032 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517638
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-33-generic root=UUID=283ff747-a721-4722-9ff8-51669dbdc2e9 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10436680 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007f66a)
[    0.000000] Memory: 2042356k/2087336k available (4675k kernel code, 43392k reserved, 2127k data, 668k init, 1177960k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a5000 - 0xc084c000   ( 668 kB)
[    0.000000]       .data : 0xc0590dc7 - 0xc07a4d88   (2127 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590dc7   (4675 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1729.375 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 3458.75 BogoMIPS (lpj=6917500)
[    0.004027] Security Framework initialized
[    0.004051] AppArmor: AppArmor initialized
[    0.004059] Mount-cache hash table entries: 512
[    0.004211] Initializing cgroup subsys ns
[    0.004217] Initializing cgroup subsys cpuacct
[    0.004222] Initializing cgroup subsys memory
[    0.004230] Initializing cgroup subsys devices
[    0.004233] Initializing cgroup subsys freezer
[    0.004236] Initializing cgroup subsys net_cls
[    0.004260] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004263] CPU: L2 cache: 1024K
[    0.004267] CPU: Physical Processor ID: 0
[    0.004269] CPU: Processor Core ID: 0
[    0.004273] mce: CPU supports 6 MCE banks
[    0.004282] CPU0: Thermal monitoring handled by SMI
[    0.004287] using mwait in idle threads.
[    0.004294] Performance Events: Core2 events, Intel PMU driver.
[    0.004304] ... version:                2
[    0.004307] ... bit width:              40
[    0.004309] ... generic registers:      2
[    0.004311] ... value mask:             000000ffffffffff
[    0.004313] ... max period:             000000007fffffff
[    0.004316] ... fixed-purpose events:   3
[    0.004318] ... event mask:             0000000700000003
[    0.004323] Checking 'hlt' instruction... OK.
[    0.023143] ACPI: Core revision 20090903
[    0.040010] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.040017] ftrace: allocating 21725 entries in 43 pages
[    0.044078] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.044430] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.084419] CPU0: Intel(R) Pentium(R) Dual  CPU  T2370  @ 1.73GHz stepping 0d
[    0.088001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.008000] CPU: L2 cache: 1024K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.008000] CPU1: Thermal monitoring handled by SMI
[    0.172082] CPU1: Intel(R) Pentium(R) Dual  CPU  T2370  @ 1.73GHz stepping 0d
[    0.172091] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.176024] Brought up 2 CPUs
[    0.176028] Total of 2 processors activated (6917.11 BogoMIPS).
[    0.176825] CPU0 attaching sched-domain:
[    0.176830]  domain 0: span 0-1 level MC
[    0.176833]   groups: 0 1
[    0.176840] CPU1 attaching sched-domain:
[    0.176843]  domain 0: span 0-1 level MC
[    0.176845]   groups: 1 0
[    0.176916] devtmpfs: initialized
[    0.176916] regulator: core version 0.5
[    0.176916] Time: 14:31:50  Date: 07/31/11
[    0.176916] NET: Registered protocol family 16
[    0.176916] Trying to unpack rootfs image as initramfs...
[    0.176916] EISA bus registered
[    0.176916] ACPI: bus type pci registered
[    0.176916] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
[    0.176916] PCI: MCFG area at f8000000 reserved in E820
[    0.176916] PCI: Using MMCONFIG for extended config space
[    0.176916] PCI: Using configuration type 1 for base access
[    0.180141] bio: create slab <bio-0> at 0
[    0.181623] ACPI: EC: Look up EC in DSDT
[    0.184535] ACPI: Executed 1 blocks of module-level executable AML code
[    0.185787] ACPI: BIOS _OSI(Linux) query ignored
[    0.188033] ACPI: EC: GPE storm detected, transactions will use polling mode
[    0.312174] ACPI: Interpreter enabled
[    0.312183] ACPI: (supports S0 S3 S4 S5)
[    0.312222] ACPI: Using IOAPIC for interrupt routing
[    0.326070] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.326166] ACPI: Power Resource [FN00] (on)
[    0.326507] ACPI: No dock devices found.
[    0.327239] ACPI Warning for \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20090903/nspredef-336)
[    0.327251] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.327379] pci 0000:00:02.0: reg 10 64bit mmio: [0x92100000-0x921fffff]
[    0.327390] pci 0000:00:02.0: reg 18 64bit mmio pref: [0x80000000-0x8fffffff]
[    0.327396] pci 0000:00:02.0: reg 20 io port: [0x5110-0x5117]
[    0.327454] pci 0000:00:02.1: reg 10 64bit mmio: [0x92200000-0x922fffff]
[    0.327585] pci 0000:00:1a.0: reg 20 io port: [0x50c0-0x50df]
[    0.327659] pci 0000:00:1a.1: reg 20 io port: [0x50a0-0x50bf]
[    0.327743] pci 0000:00:1a.7: reg 10 32bit mmio: [0x94304c00-0x94304fff]
[    0.327822] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.327828] pci 0000:00:1a.7: PME# disabled
[    0.327890] pci 0000:00:1b.0: reg 10 64bit mmio: [0x94300000-0x94303fff]
[    0.327957] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.327963] pci 0000:00:1b.0: PME# disabled
[    0.328084] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.328089] pci 0000:00:1c.0: PME# disabled
[    0.328200] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.328205] pci 0000:00:1c.4: PME# disabled
[    0.328279] pci 0000:00:1d.0: reg 20 io port: [0x5080-0x509f]
[    0.328357] pci 0000:00:1d.1: reg 20 io port: [0x5060-0x507f]
[    0.328431] pci 0000:00:1d.2: reg 20 io port: [0x5040-0x505f]
[    0.328515] pci 0000:00:1d.7: reg 10 32bit mmio: [0x94304800-0x94304bff]
[    0.328591] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.328597] pci 0000:00:1d.7: PME# disabled
[    0.328797] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 1640 (mask 000f)
[    0.328802] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0068 (mask 0007)
[    0.328862] pci 0000:00:1f.1: reg 10 io port: [0x5108-0x510f]
[    0.328872] pci 0000:00:1f.1: reg 14 io port: [0x5124-0x5127]
[    0.328881] pci 0000:00:1f.1: reg 18 io port: [0x5100-0x5107]
[    0.328891] pci 0000:00:1f.1: reg 1c io port: [0x5120-0x5123]
[    0.328900] pci 0000:00:1f.1: reg 20 io port: [0x50e0-0x50ef]
[    0.328983] pci 0000:00:1f.2: reg 10 io port: [0x50f8-0x50ff]
[    0.328992] pci 0000:00:1f.2: reg 14 io port: [0x511c-0x511f]
[    0.329001] pci 0000:00:1f.2: reg 18 io port: [0x50f0-0x50f7]
[    0.329010] pci 0000:00:1f.2: reg 1c io port: [0x5118-0x511b]
[    0.329018] pci 0000:00:1f.2: reg 20 io port: [0x5020-0x503f]
[    0.329027] pci 0000:00:1f.2: reg 24 32bit mmio: [0x94304000-0x943047ff]
[    0.329074] pci 0000:00:1f.2: PME# supported from D3hot
[    0.329079] pci 0000:00:1f.2: PME# disabled
[    0.329115] pci 0000:00:1f.3: reg 10 32bit mmio: [0x94305000-0x943050ff]
[    0.329143] pci 0000:00:1f.3: reg 20 io port: [0x5000-0x501f]
[    0.329239] pci 0000:02:00.0: reg 10 io port: [0x3000-0x30ff]
[    0.329267] pci 0000:02:00.0: reg 18 64bit mmio pref: [0x90010000-0x90010fff]
[    0.329287] pci 0000:02:00.0: reg 20 64bit mmio pref: [0x90000000-0x9000ffff]
[    0.329353] pci 0000:02:00.0: unsupported PM cap regs version (7)
[    0.329443] pci 0000:00:1c.0: bridge io port: [0x3000-0x4fff]
[    0.329449] pci 0000:00:1c.0: bridge 32bit mmio: [0x93300000-0x942fffff]
[    0.329458] pci 0000:00:1c.0: bridge 64bit mmio pref: [0x90000000-0x910fffff]
[    0.329524] pci 0000:00:1c.4: bridge io port: [0x2000-0x2fff]
[    0.329530] pci 0000:00:1c.4: bridge 32bit mmio: [0x92300000-0x932fffff]
[    0.329539] pci 0000:00:1c.4: bridge 64bit mmio pref: [0x91100000-0x920fffff]
[    0.329611] pci 0000:00:1e.0: transparent bridge
[    0.329649] pci_bus 0000:00: on NUMA node 0
[    0.329660] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.329964] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.330130] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.330257] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP5._PRT]
[    0.330503] ACPI Warning for \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20090903/nspredef-336)
[    0.336744] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 9 10 11 12)
[    0.336900] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
[    0.337049] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.337201] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.337351] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.337500] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11 12)
[    0.337650] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12)
[    0.337798] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.337962] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.337979] vgaarb: loaded
[    0.338134] SCSI subsystem initialized
[    0.338250] libata version 3.00 loaded.
[    0.338349] usbcore: registered new interface driver usbfs
[    0.338364] usbcore: registered new interface driver hub
[    0.338396] usbcore: registered new device driver usb
[    0.338561] ACPI: WMI: Mapper loaded
[    0.338563] PCI: Using ACPI for IRQ routing
[    0.338782] NetLabel: Initializing
[    0.338784] NetLabel:  domain hash size = 128
[    0.338786] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.338801] NetLabel:  unlabeled traffic allowed by default
[    0.338842] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.338850] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.338857] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.344283] Switching to clocksource tsc
[    0.346626] AppArmor: AppArmor Filesystem Enabled
[    0.346651] pnp: PnP ACPI init
[    0.346675] ACPI: bus type pnp registered
[    0.349448] pnp: PnP ACPI: found 9 devices
[    0.349451] ACPI: ACPI bus type pnp unregistered
[    0.349456] PnPBIOS: Disabled by ACPI PNP
[    0.349472] system 00:01: ioport range 0x164e-0x164f has been reserved
[    0.349476] system 00:01: ioport range 0x800-0x80f has been reserved
[    0.349480] system 00:01: ioport range 0x400-0x47f has been reserved
[    0.349483] system 00:01: ioport range 0x500-0x53f has been reserved
[    0.349488] system 00:01: iomem range 0xf8000000-0xfbffffff has been reserved
[    0.349492] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.349495] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.349499] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.349503] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.349507] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.349510] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.349519] system 00:04: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.384322] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.384328] pci 0000:00:1c.0:   IO window: 0x3000-0x4fff
[    0.384336] pci 0000:00:1c.0:   MEM window: 0x93300000-0x942fffff
[    0.384342] pci 0000:00:1c.0:   PREFETCH window: 0x00000090000000-0x000000910fffff
[    0.384351] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:08
[    0.384355] pci 0000:00:1c.4:   IO window: 0x2000-0x2fff
[    0.384363] pci 0000:00:1c.4:   MEM window: 0x92300000-0x932fffff
[    0.384369] pci 0000:00:1c.4:   PREFETCH window: 0x00000091100000-0x000000920fffff
[    0.384379] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
[    0.384381] pci 0000:00:1e.0:   IO window: disabled
[    0.384388] pci 0000:00:1e.0:   MEM window: disabled
[    0.384394] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.384425]   alloc irq_desc for 17 on node -1
[    0.384428]   alloc kstat_irqs on node -1
[    0.384437] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.384444] pci 0000:00:1c.0: setting latency timer to 64
[    0.384457] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.384463] pci 0000:00:1c.4: setting latency timer to 64
[    0.384473] pci 0000:00:1e.0: setting latency timer to 64
[    0.384479] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.384482] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.384485] pci_bus 0000:02: resource 0 io:  [0x3000-0x4fff]
[    0.384488] pci_bus 0000:02: resource 1 mem: [0x93300000-0x942fffff]
[    0.384492] pci_bus 0000:02: resource 2 pref mem [0x90000000-0x910fffff]
[    0.384495] pci_bus 0000:08: resource 0 io:  [0x2000-0x2fff]
[    0.384498] pci_bus 0000:08: resource 1 mem: [0x92300000-0x932fffff]
[    0.384501] pci_bus 0000:08: resource 2 pref mem [0x91100000-0x920fffff]
[    0.384504] pci_bus 0000:06: resource 3 io:  [0x00-0xffff]
[    0.384507] pci_bus 0000:06: resource 4 mem: [0x000000-0xffffffff]
[    0.384556] NET: Registered protocol family 2
[    0.384684] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.385102] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.385781] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.386185] TCP: Hash tables configured (established 131072 bind 65536)
[    0.386188] TCP reno registered
[    0.386327] NET: Registered protocol family 1
[    0.386355] pci 0000:00:02.0: Boot video device
[    0.386644] Simple Boot Flag at 0x44 set to 0x1
[    0.386857] cpufreq-nforce2: No nForce2 chipset.
[    0.386893] Scanning for low memory corruption every 60 seconds
[    0.387046] audit: initializing netlink socket (disabled)
[    0.387060] type=2000 audit(1312122709.383:1): initialized
[    0.398751] highmem bounce pool size: 64 pages
[    0.398758] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.400663] VFS: Disk quotas dquot_6.5.2
[    0.400748] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.401474] fuse init (API version 7.13)
[    0.401577] msgmni has been set to 1690
[    0.401853] alg: No test for stdrng (krng)
[    0.401929] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.401934] io scheduler noop registered
[    0.401937] io scheduler anticipatory registered
[    0.401939] io scheduler deadline registered
[    0.401986] io scheduler cfq registered (default)
[    0.402178]   alloc irq_desc for 24 on node -1
[    0.402181]   alloc kstat_irqs on node -1
[    0.402198] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.402211] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.402388]   alloc irq_desc for 25 on node -1
[    0.402390]   alloc kstat_irqs on node -1
[    0.402401] pcieport 0000:00:1c.4: irq 25 for MSI/MSI-X
[    0.402414] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.402533] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.402555] Firmware did not grant requested _OSC control
[    0.402586] Firmware did not grant requested _OSC control
[    0.402630] Firmware did not grant requested _OSC control
[    0.402653] Firmware did not grant requested _OSC control
[    0.402676] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.402851] ACPI: AC Adapter [ADP0] (on-line)
[    0.402948] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.402953] ACPI: Power Button [PWRB]
[    0.403003] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.406769] ACPI: Lid Switch [LID]
[    0.406843] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.406846] ACPI: Power Button [PWRF]
[    0.407050] fan PNP0C0B:00: registered as cooling_device0
[    0.407058] ACPI: Fan [FAN] (on)
[    0.407904] ACPI: SSDT 7f674c90 00232 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.408629] ACPI: SSDT 7f673610 005B3 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.409249] Monitor-Mwait will be used to enter C-1 state
[    0.409288] Monitor-Mwait will be used to enter C-2 state
[    0.409319] Monitor-Mwait will be used to enter C-3 state
[    0.409327] Marking TSC unstable due to TSC halts in idle
[    0.409404] processor LNXCPU:00: registered as cooling_device1
[    0.409863] ACPI: SSDT 7f674f10 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.410373] ACPI: SSDT 7f676d10 00083 (v01  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.410825] Switching to clocksource hpet
[    0.417465] processor LNXCPU:01: registered as cooling_device2
[    0.421034] thermal LNXTHERM:01: registered as thermal_zone0
[    0.421047] ACPI: Thermal Zone [THRM] (55 C)
[    0.423003] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.424682] brd: module loaded
[    0.425256] loop: module loaded
[    0.425372] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.425505] ata_piix 0000:00:1f.1: version 2.13
[    0.425524]   alloc irq_desc for 19 on node -1
[    0.425527]   alloc kstat_irqs on node -1
[    0.425536] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.425588] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.425695] scsi0 : ata_piix
[    0.425788] scsi1 : ata_piix
[    0.425831] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x50e0 irq 14
[    0.425835] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x50e8 irq 15
[    0.426247] Fixed MDIO Bus: probed
[    0.426290] PPP generic driver version 2.4.2
[    0.426347] tun: Universal TUN/TAP device driver, 1.6
[    0.426350] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.426455] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.426480]   alloc irq_desc for 18 on node -1
[    0.426482]   alloc kstat_irqs on node -1
[    0.426488] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.426509] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.426513] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.426550] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.426593] ehci_hcd 0000:00:1a.7: debug port 1
[    0.427117] ACPI: Battery Slot [BAT0] (battery present)
[    0.427129] isapnp: Scanning for PnP cards...
[    0.430477] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.430494] ehci_hcd 0000:00:1a.7: irq 18, io mem 0x94304c00
[    0.448079] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.448236] usb usb1: configuration #1 chosen from 1 choice
[    0.448272] hub 1-0:1.0: USB hub found
[    0.448287] hub 1-0:1.0: 4 ports detected
[    0.448367]   alloc irq_desc for 23 on node -1
[    0.448369]   alloc kstat_irqs on node -1
[    0.448377] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.448405] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.448410] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.448454] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.448497] ehci_hcd 0000:00:1d.7: debug port 1
[    0.452389] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.452408] ehci_hcd 0000:00:1d.7: irq 23, io mem 0x94304800
[    0.456668] Freeing initrd memory: 7811k freed
[    0.476027] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.476247] usb usb2: configuration #1 chosen from 1 choice
[    0.476285] hub 2-0:1.0: USB hub found
[    0.476298] hub 2-0:1.0: 6 ports detected
[    0.476381] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.476408] uhci_hcd: USB Universal Host Controller Interface driver
[    0.476471]   alloc irq_desc for 16 on node -1
[    0.476474]   alloc kstat_irqs on node -1
[    0.476482] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.476496] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.476500] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.476547] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.476589] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000050c0
[    0.476696] usb usb3: configuration #1 chosen from 1 choice
[    0.476726] hub 3-0:1.0: USB hub found
[    0.476735] hub 3-0:1.0: 2 ports detected
[    0.476790]   alloc irq_desc for 21 on node -1
[    0.476793]   alloc kstat_irqs on node -1
[    0.476798] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.476805] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.476810] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.476845] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.476882] uhci_hcd 0000:00:1a.1: irq 21, io base 0x000050a0
[    0.476993] usb usb4: configuration #1 chosen from 1 choice
[    0.477022] hub 4-0:1.0: USB hub found
[    0.477030] hub 4-0:1.0: 2 ports detected
[    0.477088] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.477095] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.477099] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.477136] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.477164] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00005080
[    0.477267] usb usb5: configuration #1 chosen from 1 choice
[    0.477299] hub 5-0:1.0: USB hub found
[    0.477309] hub 5-0:1.0: 2 ports detected
[    0.477361] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.477368] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.477372] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.477413] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.477450] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00005060
[    0.477553] usb usb6: configuration #1 chosen from 1 choice
[    0.477589] hub 6-0:1.0: USB hub found
[    0.477597] hub 6-0:1.0: 2 ports detected
[    0.477650] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.477658] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.477662] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.477703] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.477731] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00005040
[    0.477838] usb usb7: configuration #1 chosen from 1 choice
[    0.477868] hub 7-0:1.0: USB hub found
[    0.477876] hub 7-0:1.0: 2 ports detected
[    0.477995] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    0.507063] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.507071] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.507216] mice: PS/2 mouse device common for all mice
[    0.508112] rtc_cmos 00:03: RTC can wake from S4
[    0.508160] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.508191] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.508321] device-mapper: uevent: version 1.0.3
[    0.508458] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.508545] device-mapper: multipath: version 1.1.0 loaded
[    0.508548] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.508684] EISA: Probing bus 0 at eisa.0
[    0.508695] Cannot allocate resource for EISA slot 2
[    0.508698] Cannot allocate resource for EISA slot 3
[    0.508700] Cannot allocate resource for EISA slot 4
[    0.508702] Cannot allocate resource for EISA slot 5
[    0.508717] EISA: Detected 0 cards.
[    0.508891] cpuidle: using governor ladder
[    0.509030] cpuidle: using governor menu
[    0.509542] TCP cubic registered
[    0.509735] NET: Registered protocol family 10
[    0.510712] NET: Registered protocol family 17
[    0.511345] Using IPI No-Shortcut mode
[    0.511441] PM: Resume from disk failed.
[    0.511456] registered taskstats version 1
[    0.511881]   Magic number: 3:299:537
[    0.511898] bdi 1:15: hash matches
[    0.511974] rtc_cmos 00:03: setting system clock to 2011-07-31 14:31:50 UTC (1312122710)
[    0.511978] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.511980] EDD information not available.
[    0.536226] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.584044] hub 6-0:1.0: over-current change on port 2
[    0.620396] ata1.00: ATAPI: PIONEER DVD-RW  DVRKD08A, 1.51, max UDMA/33
[    0.652336] ata1.00: configured for UDMA/33
[    0.780922] isapnp: No Plug & Play device found
[    0.796066] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    0.818328] scsi 0:0:0:0: CD-ROM            PIONEER  DVD-RW  DVRKD08A 1.51 PQ: 0 ANSI: 5
[    0.942287] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.942290] Uniform CD-ROM driver Revision: 3.20
[    0.942409] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.942471] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.942561] Freeing unused kernel memory: 668k freed
[    0.943016] Write protecting the kernel text: 4676k
[    0.943078] Write protecting the kernel read-only data: 1848k
[    0.964964] udev: starting version 151
[    0.967044] usb 1-2: configuration #1 chosen from 1 choice
[    1.063227] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.063251] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.063304] r8169 0000:02:00.0: setting latency timer to 64
[    1.063365]   alloc irq_desc for 26 on node -1
[    1.063367]   alloc kstat_irqs on node -1
[    1.063386] r8169 0000:02:00.0: irq 26 for MSI/MSI-X
[    1.064175] eth0: RTL8102e at 0xf8068000, 00:1e:33:3d:d6:0d, XID 14a00000 IRQ 26
[    1.097733] ahci 0000:00:1f.2: version 3.0
[    1.097757] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.097808]   alloc irq_desc for 27 on node -1
[    1.097811]   alloc kstat_irqs on node -1
[    1.097824] ahci 0000:00:1f.2: irq 27 for MSI/MSI-X
[    1.097871] ahci: SSS flag set, parallel bus scan disabled
[    1.097905] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x3 impl SATA mode
[    1.097910] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pmp pio slum part ccc ems 
[    1.097916] ahci 0000:00:1f.2: setting latency timer to 64
[    1.111716] scsi2 : ahci
[    1.113877] scsi3 : ahci
[    1.114061] scsi4 : ahci
[    1.114222] ata3: SATA max UDMA/133 abar m2048@0x94304000 port 0x94304100 irq 27
[    1.114227] ata4: SATA max UDMA/133 abar m2048@0x94304000 port 0x94304180 irq 27
[    1.114230] ata5: DUMMY
[    1.136067] usb 2-6: new high speed USB device using ehci_hcd and address 3
[    1.283201] usb 2-6: configuration #1 chosen from 1 choice
[    1.294380] hub 3-0:1.0: over-current change on port 1
[    1.636088] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    1.814329] usb 5-1: configuration #1 chosen from 1 choice
[    1.932076] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.323943] ata3.00: ATA-8: TOSHIBA MK1246GSX, LB213M, max UDMA/100
[    2.323947] ata3.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.324958] ata3.00: configured for UDMA/100
[    2.340260] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK1246GS LB21 PQ: 0 ANSI: 5
[    2.340461] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.340586] sd 2:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    2.340640] sd 2:0:0:0: [sda] Write Protect is off
[    2.340644] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.340672] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.340832]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    2.435112] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.660071] ata4: SATA link down (SStatus 0 SControl 300)
[    2.681114] usbcore: registered new interface driver hiddev
[    2.693501] input: Trust GM-4200 Gamer Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input5
[    2.693633] generic-usb 0003:145F:011A.0001: input,hidraw0: USB HID v1.11 Mouse [Trust GM-4200 Gamer Optical Mouse] on usb-0000:00:1d.0-1/input0
[    2.693664] usbcore: registered new interface driver usbhid
[    2.693668] usbhid: v2.6:USB HID core driver
[    3.518973] EXT4-fs (sda5): mounted filesystem with ordered data mode
[   13.990047] udev: starting version 151
[   14.087600] Adding 1447928k swap on /dev/sda6.  Priority:-1 extents:1 across:1447928k 
[   14.129121] lp: driver loaded but no devices found
[   14.167663] Linux agpgart interface v0.103
[   14.171191] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[   14.171695] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[   14.324037] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x80000000
[   14.358423] Linux video capture interface: v2.00
[   14.379955] [drm] Initialized drm 1.1.0 20060810
[   14.390113] uvcvideo: Found UVC 1.00 device CNF7051 (04f2:b070)
[   14.407076] cfg80211: Calling CRDA to update world regulatory domain
[   14.422202] input: CNF7051 as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input6
[   14.422271] usbcore: registered new interface driver uvcvideo
[   14.422275] USB Video Class driver (v0.1.0)
[   14.444569] type=1505 audit(1312115524.432:2):  operation="profile_load" pid=599 name="/sbin/dhclient3"
[   14.445428] type=1505 audit(1312115524.432:3):  operation="profile_load" pid=599 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.445890] type=1505 audit(1312115524.432:4):  operation="profile_load" pid=599 name="/usr/lib/connman/scripts/dhclient-script"
[   14.449579] type=1505 audit(1312115524.436:5):  operation="profile_replace" pid=609 name="/sbin/dhclient3"
[   14.450433] type=1505 audit(1312115524.436:6):  operation="profile_replace" pid=609 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.450902] type=1505 audit(1312115524.436:7):  operation="profile_replace" pid=609 name="/usr/lib/connman/scripts/dhclient-script"
[   14.455495] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.455502] i915 0000:00:02.0: setting latency timer to 64
[   14.455786] cfg80211: World regulatory domain updated:
[   14.455791]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.455795]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.455798]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.455801]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.455804]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.455808]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.468444]   alloc irq_desc for 28 on node -1
[   14.468449]   alloc kstat_irqs on node -1
[   14.468460] i915 0000:00:02.0: irq 28 for MSI/MSI-X
[   14.468470] [drm] set up 7M of stolen space
[   14.598605] [drm] initialized overlay support
[   14.845274] phy0: Selected rate control algorithm 'minstrel'
[   14.846162] phy0: hwaddr 00:1b:9e:eb:79:3d, RTL8187BvE V0 + rtl8225z2, rfkill mask 4
[   14.868359] rtl8187: Customer ID is 0x04
[   14.868425] Registered led device: rtl8187-phy0::tx
[   14.868447] Registered led device: rtl8187-phy0::rx
[   14.870663] rtl8187: wireless switch is off
[   14.870723] usbcore: registered new interface driver rtl8187
[   15.142188] fb0: inteldrmfb frame buffer device
[   15.142192] registered panic notifier
[   15.159636] acpi device:19: registered as cooling_device3
[   15.160577] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7
[   15.162031] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[   15.162072] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   15.162130]   alloc irq_desc for 22 on node -1
[   15.162133]   alloc kstat_irqs on node -1
[   15.162142] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   15.162195] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.167782] vga16fb: initializing
[   15.167787] vga16fb: mapped to 0xc00a0000
[   15.167792] vga16fb: not registering due to another framebuffer present
[   15.239236] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x9280b1, caps: 0xa04711/0xa04000/0x0
[   15.239243] synaptics: Toshiba Satellite L350 detected, limiting rate to 40pps.
[   15.276556] hda_codec: ALC268: BIOS auto-probing.
[   15.277075] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   15.315679] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   15.322231] Console: switching to colour frame buffer device 180x56
[   15.403180] type=1505 audit(1312115525.389:8):  operation="profile_replace" pid=788 name="/sbin/dhclient3"
[   15.404054] type=1505 audit(1312115525.389:9):  operation="profile_replace" pid=788 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   15.404122] type=1505 audit(1312115525.389:10):  operation="profile_load" pid=787 name="/usr/share/gdm/guest-session/Xsession"
[   15.404557] type=1505 audit(1312115525.389:11):  operation="profile_replace" pid=788 name="/usr/lib/connman/scripts/dhclient-script"
[   15.729957] r8169: eth0: link up
[   15.729968] r8169: eth0: link up

```

---

### Post by Toz on 2011-07-31
Try the kernel parameters one at a time. If you receive a failure, this time post back the results of:```
cat /var/log/syslog | grep "PM:"
```

---

### Post by harun3d on 2011-07-31
acpi_osi=Linux did not solve the problem
acpi_osi=\"Linux\" solved the problem only for 1 time.  The second time the system did not resume after suspend.


On [the site ]("https://help.ubuntu.com/community/Grub2#Editing%20the%20GRUB%202%20Menu%20During%20Boot")where you refer to, I have read that the edits in the GNUB kernel menu works only for 1 time:
> Edits made to the menu in this manner are non-persistent. They remain in effect only for the current boot.  At next boot the edits will not work, however the second suspend mode in one session is not really a reboot of the system.  

```
cat /var/log/syslog | grep "PM:"
```gave
```

hc@hc-laptop:~$ cat /var/log/syslog | grep "PM:"
Jul 31 06:54:26 hc-laptop kernel: [18393.168832] PM: Marking nosave pages: 0000000000002000 - 0000000000006000
Jul 31 06:54:26 hc-laptop kernel: [18393.168837] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
Jul 31 06:54:26 hc-laptop kernel: [18393.168842] PM: Basic memory bitmaps created
Jul 31 13:27:57 hc-laptop kernel: [18393.168844] PM: Syncing filesystems ... done.
Jul 31 13:27:57 hc-laptop kernel: [18393.175741] PM: Preallocating image memory... done (allocated 380378 pages)
Jul 31 13:27:57 hc-laptop kernel: [18393.630882] PM: Allocated 1521512 kbytes in 0.45 seconds (3381.13 MB/s)
Jul 31 13:27:57 hc-laptop kernel: [18394.038839] PM: freeze of drv:usb dev:2-6 complete after 406.077 msecs
Jul 31 13:27:57 hc-laptop kernel: [18394.188063] PM: freeze of drv:HDA Intel dev:0000:00:1b.0 complete after 119.613 msecs
Jul 31 13:27:57 hc-laptop kernel: [18394.208818] PM: freeze of devices complete after 577.523 msecs
Jul 31 13:27:57 hc-laptop kernel: [18394.209888] PM: late freeze of devices complete after 1.065 msecs
Jul 31 13:27:57 hc-laptop kernel: [18394.228023] PM: Saving platform NVS memory
Jul 31 13:27:57 hc-laptop kernel: [18394.403126] PM: Creating hibernation image: 
Jul 31 13:27:57 hc-laptop kernel: [18394.404008] PM: Need to copy 122664 pages
Jul 31 13:27:57 hc-laptop kernel: [18394.404008] PM: Normal pages needed: 40769 + 1024, available pages: 186421
Jul 31 13:27:57 hc-laptop kernel: [18394.404008] PM: Restoring platform NVS memory
Jul 31 13:27:57 hc-laptop kernel: [18394.580506] PM: early restore of devices complete after 1.324 msecs
Jul 31 13:27:57 hc-laptop kernel: [18395.333853] PM: restore of drv:i915 dev:0000:00:02.0 complete after 692.132 msecs
Jul 31 13:27:57 hc-laptop kernel: [18395.576066] PM: restore of drv:usb dev:usb1 complete after 233.409 msecs
Jul 31 13:27:57 hc-laptop kernel: [18395.932061] PM: restore of drv:usb dev:usb2 complete after 355.980 msecs
Jul 31 13:27:57 hc-laptop kernel: [18396.180038] PM: restore of drv:usb dev:usb5 complete after 247.937 msecs
Jul 31 13:27:57 hc-laptop kernel: [18396.477194] PM: restore of drv:usb dev:1-2 complete after 290.472 msecs
Jul 31 13:27:57 hc-laptop kernel: [18396.723093] PM: restore of drv:usb dev:2-6 complete after 245.856 msecs
Jul 31 13:27:57 hc-laptop kernel: [18397.287100] PM: restore of drv:usb dev:5-1 complete after 563.976 msecs
Jul 31 13:27:57 hc-laptop kernel: [18397.362110] PM: restore of devices complete after 2741.236 msecs
Jul 31 13:27:57 hc-laptop kernel: [18397.667378] PM: Image restored successfully.
Jul 31 13:27:57 hc-laptop kernel: [18397.680314] PM: Basic memory bitmaps freed
Jul 31 13:44:45 hc-laptop kernel: [19406.405963] PM: Marking nosave pages: 0000000000002000 - 0000000000006000
Jul 31 13:44:45 hc-laptop kernel: [19406.405968] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
Jul 31 13:44:45 hc-laptop kernel: [19406.405973] PM: Basic memory bitmaps created
Jul 31 13:54:47 hc-laptop kernel: [19406.405975] PM: Syncing filesystems ... done.
Jul 31 13:54:47 hc-laptop kernel: [19406.693312] PM: Preallocating image memory... done (allocated 380380 pages)
Jul 31 13:54:47 hc-laptop kernel: [19407.271835] PM: Allocated 1521520 kbytes in 0.57 seconds (2669.33 MB/s)
Jul 31 13:54:47 hc-laptop kernel: [19407.682857] PM: freeze of drv:usb dev:2-6 complete after 408.599 msecs
Jul 31 13:54:47 hc-laptop kernel: [19407.832062] PM: freeze of drv:HDA Intel dev:0000:00:1b.0 complete after 119.614 msecs
Jul 31 13:54:47 hc-laptop kernel: [19407.860090] PM: freeze of devices complete after 587.833 msecs
Jul 31 13:54:47 hc-laptop kernel: [19407.861158] PM: late freeze of devices complete after 1.063 msecs
Jul 31 13:54:47 hc-laptop kernel: [19407.878329] PM: Saving platform NVS memory
Jul 31 13:54:47 hc-laptop kernel: [19408.051189] PM: Creating hibernation image: 
Jul 31 13:54:47 hc-laptop kernel: [19408.052009] PM: Need to copy 125286 pages
Jul 31 13:54:47 hc-laptop kernel: [19408.052009] PM: Normal pages needed: 36916 + 1024, available pages: 190274
Jul 31 13:54:47 hc-laptop kernel: [19408.052009] PM: Restoring platform NVS memory
Jul 31 13:54:47 hc-laptop kernel: [19408.228546] PM: early restore of devices complete after 1.324 msecs
Jul 31 13:54:47 hc-laptop kernel: [19409.012887] PM: restore of drv:i915 dev:0000:00:02.0 complete after 714.856 msecs
Jul 31 13:54:47 hc-laptop kernel: [19409.256065] PM: restore of drv:usb dev:usb1 complete after 234.367 msecs
Jul 31 13:54:47 hc-laptop kernel: [19409.612061] PM: restore of drv:usb dev:usb2 complete after 355.981 msecs
Jul 31 13:54:47 hc-laptop kernel: [19409.860038] PM: restore of drv:usb dev:usb5 complete after 247.939 msecs
Jul 31 13:54:47 hc-laptop kernel: [19410.157230] PM: restore of drv:usb dev:1-2 complete after 290.554 msecs
Jul 31 13:54:47 hc-laptop kernel: [19410.403006] PM: restore of drv:usb dev:2-6 complete after 245.734 msecs
Jul 31 13:54:47 hc-laptop kernel: [19410.967100] PM: restore of drv:usb dev:5-1 complete after 564.062 msecs
Jul 31 13:54:47 hc-laptop kernel: [19411.046199] PM: restore of devices complete after 2769.719 msecs
Jul 31 13:54:47 hc-laptop kernel: [19411.352406] PM: Image restored successfully.
Jul 31 13:54:47 hc-laptop kernel: [19411.374239] PM: Basic memory bitmaps freed
Jul 31 14:29:18 hc-laptop kernel: [21214.801929] PM: Marking nosave pages: 0000000000002000 - 0000000000006000
Jul 31 14:29:18 hc-laptop kernel: [21214.801933] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
Jul 31 14:29:18 hc-laptop kernel: [21214.801939] PM: Basic memory bitmaps created
Jul 31 14:29:18 hc-laptop kernel: [21214.801941] PM: Syncing filesystems ... done.
Jul 31 14:29:18 hc-laptop kernel: [21214.805375] PM: Preallocating image memory... done (allocated 380378 pages)
Jul 31 14:29:18 hc-laptop kernel: [21216.270294] PM: Allocated 1521512 kbytes in 1.46 seconds (1042.13 MB/s)
Jul 31 14:29:18 hc-laptop kernel: [21216.761744] PM: freeze of drv:sd dev:2:0:0:0 complete after 490.877 msecs
Jul 31 14:29:18 hc-laptop kernel: [21217.046869] PM: freeze of drv:usb dev:2-6 complete after 283.760 msecs
Jul 31 14:29:18 hc-laptop kernel: [21217.196063] PM: freeze of drv:HDA Intel dev:0000:00:1b.0 complete after 119.629 msecs
Jul 31 14:29:18 hc-laptop kernel: [21217.236419] PM: freeze of devices complete after 965.705 msecs
Jul 31 14:29:18 hc-laptop kernel: [21217.237492] PM: late freeze of devices complete after 1.067 msecs
Jul 31 14:29:18 hc-laptop kernel: [21217.254807] PM: Saving platform NVS memory
Jul 31 14:29:18 hc-laptop kernel: [21217.403113] PM: Creating hibernation image: 
Jul 31 14:29:18 hc-laptop kernel: [21217.404008] PM: Need to copy 117097 pages
Jul 31 14:29:18 hc-laptop kernel: [21217.404008] PM: Normal pages needed: 17325 + 1024, available pages: 209865
Jul 31 14:29:18 hc-laptop kernel: [21217.404008] PM: Restoring platform NVS memory
Jul 31 14:29:18 hc-laptop kernel: [21217.584964] PM: early restore of devices complete after 1.327 msecs
Jul 31 14:29:18 hc-laptop kernel: [21218.375390] PM: restore of drv:i915 dev:0000:00:02.0 complete after 730.883 msecs
Jul 31 14:29:18 hc-laptop kernel: [21218.621079] PM: restore of drv:usb dev:usb1 complete after 236.850 msecs
Jul 31 14:29:18 hc-laptop kernel: [21218.977078] PM: restore of drv:usb dev:usb2 complete after 355.984 msecs
Jul 31 14:29:18 hc-laptop kernel: [21219.225056] PM: restore of drv:usb dev:usb5 complete after 247.939 msecs
Jul 31 14:29:18 hc-laptop kernel: [21219.521233] PM: restore of drv:usb dev:1-2 complete after 290.321 msecs
Jul 31 14:29:18 hc-laptop kernel: [21219.768141] PM: restore of drv:usb dev:2-6 complete after 246.865 msecs
Jul 31 14:29:18 hc-laptop kernel: [21220.335127] PM: restore of drv:usb dev:5-1 complete after 566.955 msecs
Jul 31 14:29:18 hc-laptop kernel: [21220.409466] PM: restore of devices complete after 2785.856 msecs
Jul 31 14:29:18 hc-laptop kernel: [21220.715323] PM: Image restored successfully.
Jul 31 14:29:18 hc-laptop kernel: [21220.716576] PM: Basic memory bitmaps freed
Jul 31 14:32:05 hc-laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Jul 31 14:32:05 hc-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jul 31 14:32:05 hc-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jul 31 14:32:05 hc-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jul 31 14:32:05 hc-laptop kernel: [    0.511441] PM: Resume from disk failed.
Jul 31 14:32:57 hc-laptop kernel: [   42.526576] PM: Syncing filesystems ... done.
Jul 31 14:32:57 hc-laptop kernel: [   42.527834] PM: Preparing system for mem sleep
Jul 31 14:32:57 hc-laptop kernel: [   42.528736] PM: Entering mem sleep
Jul 31 14:32:57 hc-laptop kernel: [   43.302452] PM: suspend of drv:sd dev:2:0:0:0 complete after 749.295 msecs
Jul 31 14:32:57 hc-laptop kernel: [   43.628064] PM: suspend of drv:usb dev:2-6 complete after 307.962 msecs
Jul 31 14:32:57 hc-laptop kernel: [   44.066771] PM: suspend of drv:psmouse dev:serio1 complete after 422.633 msecs
Jul 31 14:32:57 hc-laptop kernel: [   44.172068] PM: suspend of drv:atkbd dev:serio0 complete after 105.291 msecs
Jul 31 14:32:57 hc-laptop kernel: [   44.444070] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 223.771 msecs
Jul 31 14:32:57 hc-laptop kernel: [   44.500365] PM: suspend of devices complete after 1971.199 msecs
Jul 31 14:32:57 hc-laptop kernel: [   44.500369] PM: suspend devices took 1.972 seconds
Jul 31 14:32:57 hc-laptop kernel: [   44.532213] PM: late suspend of devices complete after 31.839 msecs
Jul 31 14:32:57 hc-laptop kernel: [   44.875938] PM: early resume of devices complete after 1.417 msecs
Jul 31 14:32:57 hc-laptop kernel: [   45.036223] PM: resume of drv:i915 dev:0000:00:02.0 complete after 140.372 msecs
Jul 31 14:32:57 hc-laptop kernel: [   45.168071] PM: resume of drv:usb dev:usb1 complete after 130.804 msecs
Jul 31 14:32:57 hc-laptop kernel: [   45.324083] PM: resume of drv:usb dev:usb2 complete after 155.996 msecs
Jul 31 14:32:57 hc-laptop kernel: [   45.572098] PM: resume of drv:usb dev:usb5 complete after 247.976 msecs
Jul 31 14:32:57 hc-laptop kernel: [   45.869245] PM: resume of drv:usb dev:1-2 complete after 290.439 msecs
Jul 31 14:32:57 hc-laptop kernel: [   46.115072] PM: resume of drv:usb dev:2-6 complete after 245.796 msecs
Jul 31 14:32:57 hc-laptop kernel: [   46.679459] PM: resume of drv:usb dev:5-1 complete after 564.356 msecs
Jul 31 14:32:57 hc-laptop kernel: [   46.689649] PM: resume of devices complete after 1813.675 msecs
Jul 31 14:32:57 hc-laptop kernel: [   46.994837] PM: resume devices took 2.120 seconds
Jul 31 14:32:57 hc-laptop kernel: [   46.994905] PM: Finishing wakeup.
Jul 31 14:34:52 hc-laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Jul 31 14:34:52 hc-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jul 31 14:34:52 hc-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jul 31 14:34:52 hc-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jul 31 14:34:52 hc-laptop kernel: [    0.533478] PM: Resume from disk failed.
Jul 31 16:10:20 hc-laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Jul 31 16:10:20 hc-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jul 31 16:10:20 hc-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jul 31 16:10:20 hc-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jul 31 16:10:20 hc-laptop kernel: [    0.521857] PM: Resume from disk failed.
Jul 31 16:11:18 hc-laptop kernel: [   40.574532] PM: Syncing filesystems ... done.
Jul 31 16:11:18 hc-laptop kernel: [   40.575798] PM: Preparing system for mem sleep
Jul 31 16:11:18 hc-laptop kernel: [   40.576715] PM: Entering mem sleep
Jul 31 16:11:18 hc-laptop kernel: [   41.365216] PM: suspend of drv:sd dev:2:0:0:0 complete after 764.056 msecs
Jul 31 16:11:18 hc-laptop kernel: [   41.688064] PM: suspend of drv:usb dev:2-6 complete after 307.940 msecs
Jul 31 16:11:18 hc-laptop kernel: [   42.124442] PM: suspend of drv:psmouse dev:serio1 complete after 420.313 msecs
Jul 31 16:11:18 hc-laptop kernel: [   42.232048] PM: suspend of drv:atkbd dev:serio0 complete after 107.600 msecs
Jul 31 16:11:18 hc-laptop kernel: [   42.504094] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 223.807 msecs
Jul 31 16:11:18 hc-laptop kernel: [   42.553362] PM: suspend of devices complete after 1976.212 msecs
Jul 31 16:11:18 hc-laptop kernel: [   42.553366] PM: suspend devices took 1.976 seconds
Jul 31 16:11:18 hc-laptop kernel: [   42.584213] PM: late suspend of devices complete after 30.842 msecs
Jul 31 16:11:18 hc-laptop kernel: [   42.923508] PM: early resume of devices complete after 1.416 msecs
Jul 31 16:11:18 hc-laptop kernel: [   43.084223] PM: resume of drv:i915 dev:0000:00:02.0 complete after 140.463 msecs
Jul 31 16:11:18 hc-laptop kernel: [   43.216073] PM: resume of drv:usb dev:usb1 complete after 130.805 msecs
Jul 31 16:11:18 hc-laptop kernel: [   43.373081] PM: resume of drv:usb dev:usb2 complete after 156.992 msecs
Jul 31 16:11:18 hc-laptop kernel: [   43.620106] PM: resume of drv:usb dev:usb5 complete after 246.986 msecs
Jul 31 16:11:18 hc-laptop kernel: [   43.917245] PM: resume of drv:usb dev:1-2 complete after 291.996 msecs
Jul 31 16:11:18 hc-laptop kernel: [   44.163055] PM: resume of drv:usb dev:2-6 complete after 245.767 msecs
Jul 31 16:11:18 hc-laptop kernel: [   44.728445] PM: resume of drv:usb dev:5-1 complete after 565.359 msecs
Jul 31 16:11:18 hc-laptop kernel: [   44.739245] PM: resume of devices complete after 1815.703 msecs
Jul 31 16:11:18 hc-laptop kernel: [   45.046317] PM: resume devices took 2.124 seconds
Jul 31 16:11:18 hc-laptop kernel: [   45.046386] PM: Finishing wakeup.
Jul 31 16:28:58 hc-laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Jul 31 16:28:58 hc-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jul 31 16:28:58 hc-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jul 31 16:28:58 hc-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jul 31 16:28:58 hc-laptop kernel: [    0.529497] PM: Resume from disk failed.
Jul 31 16:56:50 hc-laptop kernel: [  142.845448] PM: Syncing filesystems ... done.
Jul 31 16:56:50 hc-laptop kernel: [  142.846904] PM: Preparing system for mem sleep
Jul 31 16:56:50 hc-laptop kernel: [  142.847886] PM: Entering mem sleep
Jul 31 16:56:50 hc-laptop kernel: [  143.583086] PM: suspend of drv:sd dev:2:0:0:0 complete after 706.924 msecs
Jul 31 16:56:50 hc-laptop kernel: [  143.908066] PM: suspend of drv:usb dev:2-6 complete after 307.948 msecs
Jul 31 16:56:50 hc-laptop kernel: [  144.345245] PM: suspend of drv:psmouse dev:serio1 complete after 421.119 msecs
Jul 31 16:56:50 hc-laptop kernel: [  144.452069] PM: suspend of drv:atkbd dev:serio0 complete after 106.818 msecs
Jul 31 16:56:50 hc-laptop kernel: [  144.724091] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 223.805 msecs
Jul 31 16:56:50 hc-laptop kernel: [  144.789370] PM: suspend of devices complete after 1941.035 msecs
Jul 31 16:56:50 hc-laptop kernel: [  144.789374] PM: suspend devices took 1.944 seconds
Jul 31 16:56:50 hc-laptop kernel: [  144.820213] PM: late suspend of devices complete after 30.834 msecs
Jul 31 16:56:50 hc-laptop kernel: [  145.164350] PM: early resume of devices complete after 1.425 msecs
Jul 31 16:56:50 hc-laptop kernel: [  145.328223] PM: resume of drv:i915 dev:0000:00:02.0 complete after 142.383 msecs
Jul 31 16:56:50 hc-laptop kernel: [  145.460072] PM: resume of drv:usb dev:usb1 complete after 130.804 msecs
Jul 31 16:56:50 hc-laptop kernel: [  145.617069] PM: resume of drv:usb dev:usb2 complete after 156.982 msecs
Jul 31 16:56:50 hc-laptop kernel: [  145.864107] PM: resume of drv:usb dev:usb5 complete after 246.999 msecs
Jul 31 16:56:50 hc-laptop kernel: [  146.161242] PM: resume of drv:usb dev:1-2 complete after 291.941 msecs
Jul 31 16:56:50 hc-laptop kernel: [  146.407054] PM: resume of drv:usb dev:2-6 complete after 245.770 msecs
Jul 31 16:56:50 hc-laptop kernel: [  146.970445] PM: resume of drv:usb dev:5-1 complete after 563.360 msecs
Jul 31 16:56:50 hc-laptop kernel: [  146.976130] PM: resume of devices complete after 1811.746 msecs
Jul 31 16:56:50 hc-laptop kernel: [  147.281316] PM: resume devices took 2.116 seconds
Jul 31 16:56:50 hc-laptop kernel: [  147.281384] PM: Finishing wakeup.
Jul 31 17:09:39 hc-laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Jul 31 17:09:39 hc-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jul 31 17:09:39 hc-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jul 31 17:09:39 hc-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jul 31 17:09:39 hc-laptop kernel: [    0.520218] PM: Resume from disk failed.

```Maybe I have to undo my first actions to solve the suspend problem.  As I said in my first post, I did the following
```
      sudo gedit /etc/default/acpi-support 
``` go to POST_VIDEO=
 and set it POST_VIDEO=false

It did not solve the problem.  Then I tried:
```
      sudo gedit /etc/pm/config.d/00sleep_module 
```Add a line at the end of file &#8216;SUSPEND_MODULES=&#8221;xhci&#8221; (file was empty)

Do I have to undo this?

---

### Post by Toz on 2011-07-31
Since we're having some luck with **acpi_osi=\"Linux\" **, let's make it permanent.

1. ```
gksudo gedit /etc/default/grub
```
and add to the end of the line starting "GRUB_CMDLINE_LINUX_DEFAULT" (inside the quotes) the parameter.
For example, mine says:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
To change it, I would make it look like:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\"Linux\""
Note: your line may look different. The important part is that we add the kernel parameter at the end of that line, inside of the last quote.

2. Update the grub configuration:
```
sudo update-grub
```

3. Undo the change that you made to /etc/default/acpi-support (lets not worry about the other change yet - if anything, it will probably be helpful and won't hurt)

4. Reboot

5. Suspend/Resume. Does it work?

6. Suspend/Resume again. Does it work?
If not, post back the contents of **/var/log/pm-suspend.log**, **/etc/default/grub** and the results of:
```
cat /var/log/syslog | grep "PM:"
```

---

### Post by harun3d on 2011-08-01
I did the steps.  I tried the suspend mode three times.  Only the second time resuming worked.


content of **/var/log/pm-suspend.log**:
```

Initial commandline parameters: 
Mon Aug  1 07:15:30 CEST 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux hc-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
joydev                  8740  0 
binfmt_misc             6587  1 
snd_hda_codec_realtek   203376  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
ppdev                   5259  0 
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rtl8187                50680  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              205402  1 rtl8187
led_class               2864  1 rtl8187
i915                  288611  3 
drm_kms_helper         29329  1 i915
cfg80211              126144  2 rtl8187,mac80211
eeprom_93cx6            1333  1 rtl8187
uvcvideo               57374  0 
drm                   162377  4 i915,drm_kms_helper
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63677  0 
serio_raw               3978  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
intel_agp              24375  2 i915
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
r8169                  34140  0 
mii                     4381  1 r8169
ahci                   32360  2 
             total       used       free     shared    buffers     cached
Mem:       2051944     699548    1352396          0      82500     313524
-/+ buffers/cache:     303524    1748420
Swap:      1447928          0    1447928
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/70QuteCom suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:success.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Mon Aug  1 07:15:32 CEST 2011: performing suspend
Mon Aug  1 07:22:20 CEST 2011: Awake.
Mon Aug  1 07:22:20 CEST 2011: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend:success.
/usr/lib/pm-utils/sleep.d/99video resume suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:success.
/usr/lib/pm-utils/sleep.d/95led resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend:success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend:success.
/usr/lib/pm-utils/sleep.d/70QuteCom resume suspend:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:success.
/etc/pm/sleep.d/10_grub-common resume suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend:success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend:success.
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:success.
Mon Aug  1 07:22:25 CEST 2011: Finished.
Initial commandline parameters: 
Mon Aug  1 07:24:11 CEST 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux hc-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
joydev                  8740  0 
binfmt_misc             6587  1 
snd_hda_codec_realtek   203376  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
ppdev                   5259  0 
arc4                    1153  2 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rtl8187                50680  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              205402  1 rtl8187
led_class               2864  1 rtl8187
i915                  288611  3 
drm_kms_helper         29329  1 i915
cfg80211              126144  2 rtl8187,mac80211
eeprom_93cx6            1333  1 rtl8187
uvcvideo               57374  0 
drm                   162377  4 i915,drm_kms_helper
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63677  0 
serio_raw               3978  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
intel_agp              24375  2 i915
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
r8169                  34140  0 
mii                     4381  1 r8169
ahci                   32360  2 
             total       used       free     shared    buffers     cached
Mem:       2051944     697220    1354724          0      82660     315292
-/+ buffers/cache:     299268    1752676
Swap:      1447928          0    1447928
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/70QuteCom suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:success.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Mon Aug  1 07:24:12 CEST 2011: performing suspend
Initial commandline parameters: 
Mon Aug  1 07:50:13 CEST 2011: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:Linux hc-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
joydev                  8740  0 
snd_hda_codec_realtek   203376  1 
arc4                    1153  2 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
ppdev                   5259  0 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rtl8187                50680  0 
mac80211              205402  1 rtl8187
led_class               2864  1 rtl8187
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  288611  3 
drm_kms_helper         29329  1 i915
cfg80211              126144  2 rtl8187,mac80211
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
eeprom_93cx6            1333  1 rtl8187
uvcvideo               57374  0 
drm                   162377  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
intel_agp              24375  2 i915
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
psmouse                63677  0 
serio_raw               3978  0 
video                  17375  1 i915
output                  1871  1 video
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169
             total       used       free     shared    buffers     cached
Mem:       2051944     370060    1681884          0      80484     166316
-/+ buffers/cache:     123260    1928684
Swap:      1447928          0    1447928
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/70QuteCom hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate:success.
/etc/pm/sleep.d/action_wpa hibernate hibernate:success.
Mon Aug  1 07:50:15 CEST 2011: performing hibernate
Mon Aug  1 08:09:07 CEST 2011: Awake.
Mon Aug  1 08:09:07 CEST 2011: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/70QuteCom thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:success.
/etc/pm/sleep.d/10_grub-common thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:success.
Mon Aug  1 08:09:12 CEST 2011: Finished.

```content of [B]/etc/default/grub:

[/B]```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\"Linux\""
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

``````
cat /var/log/syslog | grep "PM:"
``` gave
```

hc@hc-laptop:~$ cat /var/log/syslog | grep "PM:"
Aug  1 07:22:20 hc-laptop kernel: [ 7574.580843] PM: Syncing filesystems ... done.
Aug  1 07:22:20 hc-laptop kernel: [ 7574.583940] PM: Preparing system for mem sleep
Aug  1 07:22:20 hc-laptop kernel: [ 7574.584918] PM: Entering mem sleep
Aug  1 07:22:20 hc-laptop kernel: [ 7575.271068] PM: suspend of drv:sd dev:2:0:0:0 complete after 662.922 msecs
Aug  1 07:22:20 hc-laptop kernel: [ 7575.624062] PM: suspend of drv:usb dev:2-6 complete after 352.963 msecs
Aug  1 07:22:20 hc-laptop kernel: [ 7576.061476] PM: suspend of drv:psmouse dev:serio1 complete after 421.344 msecs
Aug  1 07:22:20 hc-laptop kernel: [ 7576.168062] PM: suspend of drv:atkbd dev:serio0 complete after 106.580 msecs
Aug  1 07:22:20 hc-laptop kernel: [ 7576.440072] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 223.784 msecs
Aug  1 07:22:20 hc-laptop kernel: [ 7576.516358] PM: suspend of devices complete after 1931.024 msecs
Aug  1 07:22:20 hc-laptop kernel: [ 7576.516363] PM: suspend devices took 1.936 seconds
Aug  1 07:22:20 hc-laptop kernel: [ 7576.548201] PM: late suspend of devices complete after 31.833 msecs
Aug  1 07:22:20 hc-laptop kernel: [ 7576.866330] PM: early resume of devices complete after 1.410 msecs
Aug  1 07:22:20 hc-laptop kernel: [ 7577.028208] PM: resume of drv:i915 dev:0000:00:02.0 complete after 141.233 msecs
Aug  1 07:22:20 hc-laptop kernel: [ 7577.160060] PM: resume of drv:usb dev:usb1 complete after 130.819 msecs
Aug  1 07:22:20 hc-laptop kernel: [ 7577.292057] PM: resume of drv:usb dev:usb2 complete after 131.981 msecs
Aug  1 07:22:20 hc-laptop kernel: [ 7577.589178] PM: resume of drv:usb dev:1-2 complete after 289.408 msecs
Aug  1 07:22:20 hc-laptop kernel: [ 7577.835009] PM: resume of drv:usb dev:2-6 complete after 245.800 msecs
Aug  1 07:22:20 hc-laptop kernel: [ 7578.155411] PM: resume of drv:sd dev:2:0:0:0 complete after 320.367 msecs
Aug  1 07:22:20 hc-laptop kernel: [ 7578.155583] PM: resume of devices complete after 1289.220 msecs
Aug  1 07:22:20 hc-laptop kernel: [ 7578.460751] PM: resume devices took 1.596 seconds
Aug  1 07:22:20 hc-laptop kernel: [ 7578.460820] PM: Finishing wakeup.
Aug  1 07:49:25 hc-laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Aug  1 07:49:25 hc-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Aug  1 07:49:25 hc-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Aug  1 07:49:25 hc-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Aug  1 07:49:25 hc-laptop kernel: [    0.495825] PM: Resume from disk failed.
Aug  1 08:09:07 hc-laptop kernel: [   68.897593] PM: Marking nosave pages: 0000000000002000 - 0000000000006000
Aug  1 08:09:07 hc-laptop kernel: [   68.897598] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
Aug  1 08:09:07 hc-laptop kernel: [   68.897603] PM: Basic memory bitmaps created
Aug  1 08:09:07 hc-laptop kernel: [   68.897605] PM: Syncing filesystems ... done.
Aug  1 08:09:07 hc-laptop kernel: [   68.899839] PM: Preallocating image memory... done (allocated 102477 pages)
Aug  1 08:09:07 hc-laptop kernel: [   69.006598] PM: Allocated 409908 kbytes in 0.10 seconds (4099.08 MB/s)
Aug  1 08:09:07 hc-laptop kernel: [   69.366820] PM: freeze of drv:usb dev:2-6 complete after 294.411 msecs
Aug  1 08:09:07 hc-laptop kernel: [   69.620085] PM: freeze of drv:HDA Intel dev:0000:00:1b.0 complete after 223.611 msecs
Aug  1 08:09:07 hc-laptop kernel: [   69.660348] PM: freeze of devices complete after 653.352 msecs
Aug  1 08:09:07 hc-laptop kernel: [   69.661301] PM: late freeze of devices complete after 0.946 msecs
Aug  1 08:09:07 hc-laptop kernel: [   69.675024] PM: Saving platform NVS memory
Aug  1 08:09:07 hc-laptop kernel: [   69.847143] PM: Creating hibernation image: 
Aug  1 08:09:07 hc-laptop kernel: [   69.848010] PM: Need to copy 102019 pages
Aug  1 08:09:07 hc-laptop kernel: [   69.848010] PM: Normal pages needed: 36658 + 1024, available pages: 190532
Aug  1 08:09:07 hc-laptop kernel: [   69.848010] PM: Restoring platform NVS memory
Aug  1 08:09:07 hc-laptop kernel: [   69.996727] PM: early restore of devices complete after 1.311 msecs
Aug  1 08:09:07 hc-laptop kernel: [   70.772211] PM: restore of drv:i915 dev:0000:00:02.0 complete after 718.736 msecs
Aug  1 08:09:07 hc-laptop kernel: [   71.016059] PM: restore of drv:usb dev:usb1 complete after 235.009 msecs
Aug  1 08:09:07 hc-laptop kernel: [   71.252060] PM: restore of drv:usb dev:usb2 complete after 235.986 msecs
Aug  1 08:09:07 hc-laptop kernel: [   71.549188] PM: restore of drv:usb dev:1-2 complete after 290.036 msecs
Aug  1 08:09:07 hc-laptop kernel: [   71.795090] PM: restore of drv:usb dev:2-6 complete after 245.871 msecs
Aug  1 08:09:07 hc-laptop kernel: [   72.088854] PM: restore of drv:sd dev:2:0:0:0 complete after 293.730 msecs
Aug  1 08:09:07 hc-laptop kernel: [   72.089026] PM: restore of devices complete after 2057.127 msecs
Aug  1 08:09:07 hc-laptop kernel: [   72.394269] PM: Image restored successfully.
Aug  1 08:09:07 hc-laptop kernel: [   72.398316] PM: Basic memory bitmaps freed
hc@hc-laptop:~$ 

```

---

### Post by Toz on 2011-08-01
According to your pm-suspend log file, the thirds attempt was a hibernate attempt. Is this correct?

Can you try the uswsusp package?
```
sudo apt-get install uswsusp
```
After it's installed, from a terminal window, run:
```
sudo s2ram
```
If you get an error message about not being in the whitelist, run:
```
sudo s2ram -f
```

---

### Post by harun3d on 2011-08-04
It is possible that the third one was a hibernate action. But the important thing is: in many cases resuming do not work.  If I have tried suspending/resuming many times, then I do hibernate to avoid forced shut down.  I did maybe 20 forced shut downs in two weeks.     

I installed the package.  I did sudo s2ram.  It gave an error message:
```

hc@hc-laptop:~$ sudo s2ram
[sudo] password for hc: 
Machine is unknown.
This machine can be identified by:
    sys_vendor   = "TOSHIBA"
    sys_product  = "Satellite L350"
    sys_version  = "PSLD0E-005003BT"
    bios_version = "1.40"
See http://suspend.sf.net/s2ram-support.html for details.

If you report a problem, please include the complete output above.

```But sudo s2ram -f worked for suspending.  But when I tried to resume, in many cases resuming did not work like always.

---

### Post by Toz on 2011-08-04
According to your previous logs, suspend/resume works with the exception that the display doesn't return to the screen. I was hoping s2ram would have helped. From [http://en.opensuse.org/SDB:Suspend_to_RAM]("http://en.opensuse.org/SDB:Suspend_to_RAM"), can you try the following combinations of s2ram to see if it will restore the screen?
```
s2ram -f -a 3
s2ram -f -a 2
s2ram -f -a 1
s2ram -f -p -m
s2ram -f -p -s
s2ram -f -m
s2ram -f -s
s2ram -f -p
s2ram -f -a 1 -m
s2ram -f -a 1 -s
```

If none of those work, try one more suspend, normally. On resume, when you get the blank screen, try going to another vt and back. To do so, press Ctrl+Alt+F1, then Ctrl+Alt+F7 to return. Does the backlight come back on?

And also, if your brightness keys work, try adjusting them as well after resume.

---

### Post by harun3d on 2011-08-07
I typed
```
s2ram -f -a 3
``` it gave an error

```
hc@hc-laptop:~$ s2ram -f -a 3
fgconsole: getconsolefd: Invalid argument
Switching from vt-1 to vt1
chvt: VT_ACTIVATE: Bad file descriptor
VT_WAITACTIVE: Bad file descriptor
Segmentation fault

```Without trying suspend mode (because of the error), I typed

```
 s2ram -f -a 2
``` It gave the same error.
I typed all the following lines one by one.  They gave all the same error one by one.
```

s2ram -f -a 1
s2ram -f -p -m
s2ram -f -p -s
s2ram -f -m
s2ram -f -s
s2ram -f -p
s2ram -f -a 1 -m
s2ram -f -a 1 -s

s2ram -f -a 3 -v
s2ram -f -a 2 -v
s2ram -f -a 1 -v
s2ram -f -p -m -v
s2ram -f -p -s -v
s2ram -f -m -v
s2ram -f -s -v
s2ram -f -p -v
s2ram -f -a 1 -m -v
s2ram -f -a 1 -s -v


```I tried the suspend mode.  The laptop did not resume.  I forced the shut down the laptop.  A memory check was done after the startup.

I did not try the suspend mode (with suspend key) after every line of code.  Should I? The code s2ram should activate the suspend mode.  

Or should I write ```
sudo s2ram ... 
```instead of ```
s2ram ...
``` only?

> If none of those work, try one more suspend, normally. On resume, when you get the blank screen, try going to another vt and back. To do so, press Ctrl+Alt+F1, then Ctrl+Alt+F7 to return. Does the backlight come back on?I pressed Ctrl+Alt+F1 and Ctrl+Alt+F7 when resuming failed, but the screen did not turn on.

```
And also, if your brightness keys work, try adjusting them as well after resume.
```I did.  Still resuming problems.

---

### Post by Toz on 2011-08-07
Yes, you need to run all those s2ram commands with sudo - you need root privileges. If it works, we can change that later.

---

### Post by harun3d on 2011-08-08
```
sudo s2ram -f -a 3
```suspended the system but resuming was impossible 

An advice of  a site: check the num lock led:this could be a hint to decide which problem it is: 
  ```

                               num lock led                                  wireless led
before suspend:                      ON                                         ON
intention to resume:                 OFF                                        ON


```so wireless button works but the num lock button do not.


Ctrl Alt F7 and Ctrl Alt F1 do not help

I will check other codes after my vacation (after one month).

---

### Post by harun3d on 2011-10-24
I have tried most of the codes, not all of them because I need to do a forced shut down due to the fact that my computer does not resume after suspend.  I have done dozens of forced shut downs.  If try more codes I will probably destroy my computer instead of solving the suspend problem.  

I have installed some packages that provides suspend mode.  It did not help.

The backlight of the screen goes on but I do not see anything on screen.  Num Lock Led works after suspend.

So as result: SUSPEND MODE DOES NOT WORK in LINUX.  But I keep on using Linux.

---

### Post by pmguerre on 2011-12-05
Suspend DOES WORK ON LINUX! :)

It appears that kernel 2.6.35 introduced a "new bug" to some machines...

Try this (from [http://wiki.archlinux.org/index.php/Pm-utils#Reboot_instead_of_resume_from_suspend](http://wiki.archlinux.org/index.php/Pm-utils#Reboot_instead_of_resume_from_suspend))

> **Reboot instead of resume from suspend **
 
 This problem started when saving NVS area during suspend was introduced (in 2.6.35-rc4) ([mailing list post]("http://www.spinics.net/lists/linux-acpi/msg29521.html")).  However, it is known that this mechanism does not work on all machines,  so the kernel developers allow the user to disable it with the help of  the [COLOR=#222][FONT=monospace]acpi_sleep=nonvs[/FONT][/COLOR] kernel command line option. This option could be pass to the kernel through [GRUB]("https://wiki.archlinux.org/index.php/GRUB") options by editing the file [COLOR=#222][FONT=monospace]/boot/grub/menu.lst[/FONT][/COLOR] (GRUB 0.97) on the [COLOR=#222][FONT=monospace]kernel[/FONT][/COLOR] line.hope it helps

---

### Post by harun3d on 2012-06-13
[http://wiki.archlinux.org/index.php/...e_from_suspend]("http://wiki.archlinux.org/index.php/Pm-utils#Reboot_instead_of_resume_from_suspend") says: 
> editing the file /boot/grub/menu.lst (GRUB 0.97) on the kernel line. How? Adding which text?

Also the following text is too concise to understand for someone who is not a  software engineer
> **  Blank screen when waking from suspend **

 Some laptops (e.g Dell Inspiron Mini 1018) will just show a black  screen with no backlight after resuming from suspend. If this happens to  you, try going into the BIOS of the laptop and disabling Intel  SpeedStep if it is present. 
You could also try, without disabling SpeedStep, creating a quirk in /etc/pm/sleep.d/ with this content (requires [FONT=monospace][vbetool]("https://www.archlinux.org/packages/?name=vbetool")[/FONT]): 

#!/bin/sh
#
case "$1" in
suspend)
;;
resume)
sleep 5
vbetool dpms off
vbetool dpms on
;;
*) exit $NA
;;
esac

save it as you want but with a 00 in front of the name so this is called last when resuming; remember to chmod +x the script. Try adjusting the sleep time if the other commands are called too soon, or if it works well, you can also try removing that line. 


---

### Post by icegood on 2012-07-11
Have same issue as TS
```

uname -a

```
says 
```

Linux ubuntu 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

```

lspci -vnn

```
says:
```

00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS880 Host Bridge [1022:9601]
    Subsystem: ASUSTeK Computer Inc. Device [1043:1bf2]
    Flags: bus master, 66MHz, medium devsel, latency 32
    Capabilities: [c4] HyperTransport: Slave or Primary Interface
    Capabilities: [54] HyperTransport: UnitID Clumping
    Capabilities: [40] HyperTransport: Retry Mode
    Capabilities: [9c] HyperTransport: #1a
    Capabilities: [f8] HyperTransport: #1c

00:02.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0) [1022:9603] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=03, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fdf00000-fe8fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device [1043:1bf2]
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [110] Virtual Channel
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0) [1022:9604] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Memory behind bridge: fea00000-feafffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device [1043:1bf2]
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [110] Virtual Channel
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1) [1022:9605] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fe900000-fe9fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device [1043:1bf2]
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [110] Virtual Channel
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:11.0 SATA controller [0106]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391] (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device [1043:1313]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 43
    I/O ports at f090 [size=8]
    I/O ports at f080 [size=4]
    I/O ports at f070 [size=8]
    I/O ports at f060 [size=4]
    I/O ports at f050 [size=16]
    Memory at feb0a000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] MSI: Enable+ Count=1/4 Maskable- 64bit+
    Capabilities: [70] SATA HBA v1.0
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: ahci

00:12.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device [1043:1313]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb09000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device [1043:1313]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at feb08000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:13.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device [1043:1313]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb07000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device [1043:1313]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at feb06000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller [1002:4385] (rev 41)
    Flags: 66MHz, medium devsel
    Kernel driver in use: piix4_smbus
    Kernel modules: sp5100_tco, i2c-piix4

00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
    Subsystem: ASUSTeK Computer Inc. Device [1043:11b3]
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at feb00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1313]
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge [1002:4384] (rev 40) (prog-if 01 [Subtractive decode])
    Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=64

00:16.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device [1043:1313]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb05000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:16.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device [1043:1313]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at feb04000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
    Flags: fast devsel
    Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
    Flags: fast devsel

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
    Flags: fast devsel
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
    Flags: fast devsel
    Capabilities: [f0] Secure device <?>
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
    Flags: fast devsel

01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Manhattan [Mobility Radeon HD 5400 Series] [1002:68e0] (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device [1043:1bf2]
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fdf20000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at e000 [size=256]
    Expansion ROM at fdf00000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx_updates, radeon

01:00.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI Cedar HDMI Audio [Radeon HD 5400/6300 Series] [1002:aa68]
    Subsystem: ASUSTeK Computer Inc. Device [1043:1bf2]
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at fdf40000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

04:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fea00000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [60] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 00-15-17-ff-ff-24-14-12
    Capabilities: [170] Power Budgeting <?>
    Kernel driver in use: ath9k
    Kernel modules: ath9k

05:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382] (rev 80)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1a07]
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fe907000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

05:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381] (rev 80) (prog-if 01)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1a07]
    Flags: fast devsel, IRQ 18
    Memory at fe906000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel modules: sdhci-pci

05:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383] (rev 80)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1a07]
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fe905000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: jmb38x_ms
    Kernel modules: jmb38x_ms

05:00.4 System peripheral [0880]: JMicron Technology Corp. xD Host Controller [197b:2384] (rev 80)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1a07]
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at fe904000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-

05:00.5 Ethernet controller [0200]: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller [197b:0250] (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1905]
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at fe900000 (32-bit, non-prefetchable) [size=16K]
    I/O ports at d100 [size=128]
    I/O ports at d000 [size=256]
    Capabilities: [68] Power Management version 3
    Capabilities: [50] Express Legacy Endpoint, MSI 00
    Capabilities: [40] MSI-X: Enable- Count=8 Masked-
    Capabilities: [70] MSI: Enable+ Count=1/8 Maskable+ 64bit+
    Kernel driver in use: jme
    Kernel modules: jme

```

```
dmidecode -s system-manufacturer

```
says:
```

ASUSTeK Computer Inc.

```

```

dmidecode -s system-product-name

```
says:
```

K52Dr

```
====================================
```

cat /var/log/pm-suspend.log | gedit

```
says
```

Initial commandline parameters: --quirk-dpms-suspend
&#1057;&#1088;. &#1080;&#1102;&#1083;&#1103; 11 12:03:23 EEST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux ubuntu 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
bnep                   18281  2 
parport_pc             32866  0 
rfcomm                 47604  0 
ppdev                  17113  0 
bluetooth             180104  10 bnep,rfcomm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223867  1 
snd_hda_intel          33773  5 
arc4                   12529  2 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
ath9k                 132390  0 
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
fglrx                3263886  97 
mac80211              506816  1 ath9k
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
joydev                 17693  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
ath9k_common           14053  1 ath9k
snd_timer              29990  2 snd_pcm,snd_seq
ath9k_hw              411112  2 ath9k,ath9k_common
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
sp5100_tco             13791  0 
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
soundcore              15091  1 snd
i2c_piix4              13301  0 
jmb38x_ms              17646  0 
cfg80211              205544  3 ath9k,mac80211,ath
psmouse                87692  0 
edac_core              53746  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
k10temp                13166  0 
v4l2_compat_ioctl32    17128  1 videodev
edac_mce_amd           23709  0 
memstick               16569  1 jmb38x_ms
serio_raw              13211  0 
asus_laptop            24493  0 
video                  19596  0 
sparse_keymap          13890  1 asus_laptop
mac_hid                13253  0 
input_polldev          13896  1 asus_laptop
usbhid                 47199  0 
hid                    99559  1 usbhid
jme                    41259  0 
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
             total       used       free     shared    buffers     cached
Mem:       4048232    2221464    1826768          0     787700     873680
-/+ buffers/cache:     560084    3488148
Swap:       262140          0     262140

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'wlan0'
OK

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
ATI Catalyst driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
&#1057;&#1088;. &#1080;&#1102;&#1083;&#1103; 11 12:03:26 EEST 2012: performing suspend

```

So, you can see all those quirks for video are rejected by ATI Catalyst driver.
==============================
General behaviour:
screen firstly is off then turned on with blinking cursor on (0,0) coordinate.

---

### Post by Toz on 2012-07-11
@icegood,
Give this fix a try: [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug"). According to the comments, it works on similar systems.

---

### Post by icegood on 2012-07-11
> **Toz said:**
> @icegood,
Give this fix a try: [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug). According to the comments, it works on similar systems.
Yes! That stuff work for me too!

---

### Post by chronos00 on 2013-05-31
> **Toz said:**
> According to your pm-suspend log file, the thirds attempt was a hibernate attempt. Is this correct?

Can you try the uswsusp package?
```
sudo apt-get install uswsusp
```
After it's installed, from a terminal window, run:
```
sudo s2ram
```
If you get an error message about not being in the whitelist, run:
```
sudo s2ram -f
```

Thank you Toz! Really deluxe support!

In my case, suspending also also stopped working after a recent update. My Samsung laptop would suspend, but not resume afterwards; it would just stay blank. 
Installing uswsusp solved the problem, and restored suspend functionality.

Thank you again.
Regards.

---

