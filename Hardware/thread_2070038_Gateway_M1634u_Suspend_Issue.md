---
title: "Gateway M1634u Suspend Issue"
date: 2012-10-11
forum: Hardware
---

### Post by db2k on 2012-10-11
I'm having this same issue and I've been googling all day to try and find a fix to no avail.

The laptop is a Gateway M-1634u.  The graphics card is an ATI, and I believe it is no longer supported (though the linux driver seems to work just fine. )

The screen is entirely black and I don't not have a cursor as some people ae reporting. I'm unable to change to the commandline via (ctrl) alt+F1 (or f2, f3, and so on). Nor does the function key to change monitors do anything (it was worth a shot I guess).

I haven't edited my grub file as the post earlier in this thread suggests. Should I?

The ONLY thing i've found that KIND of works is to switch the action for when the lid closes to "do nothing", as it can't wake up from either suspend or hibernate

Any ideas?

Here are the results of the following commands: 
cat /proc/cmdline lsmod sudo lspci -vnn | grep -A10 VGA

```
dann@dann-laptop:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-lowlatency root=UUID=f8d0bdd9-3c44-47c0-a765-2f5d1b2a195e ro acpi_osi=Linux quiet splash acpi_backlight=vendor vt.handoff=7
```
```
dann@dann-laptop:~$ lsmod
Module                  Size  Used by
btrfs                 632603  0 
zlib_deflate           25725  1 btrfs
libcrc32c              12426  1 btrfs
ufs                    73994  0 
qnx4                   17398  0 
hfsplus                83863  0 
hfs                    53950  0 
minix                  35645  0 
ntfs                   98239  0 
msdos                  17046  0 
jfs                   178715  0 
xfs                   761976  0 
reiserfs              237368  0 
ext2                   71675  0 
nls_iso8859_1          12461  1 
nls_cp437              16553  1 
vfat                   17259  1 
fat                    57785  2 msdos,vfat
arc4                   12458  2 
bnep                   17574  2 
rfcomm                 46036  0 
bluetooth             168989  10 bnep,rfcomm
parport_pc             30822  0 
ppdev                  16865  0 
vesafb                 12597  1 
snd_hda_codec_hdmi     31064  1 
snd_hda_codec_idt      62361  1 
joydev                 17257  0 
snd_hda_intel          30717  4 
snd_hda_codec          99443  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17255  1 snd_hda_codec
snd_pcm                84403  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           12848  0 
uvcvideo               71008  0 
videodev               83376  1 uvcvideo
v4l2_compat_ioctl32    16887  1 videodev
snd_rawmidi            27093  1 snd_seq_midi
snd_seq_midi_event     13316  1 snd_seq_midi
psmouse                78176  0 
snd_seq                57369  2 snd_seq_midi,snd_seq_midi_event
snd_timer              27226  2 snd_pcm,snd_seq
snd_seq_device         13175  3 snd_seq_midi,snd_rawmidi,snd_seq
r8187se               174868  0 
sp5100_tco             12958  0 
i2c_piix4              12670  0 
serio_raw              12845  0 
eeprom_93cx6           12360  1 r8187se
snd                    65336  18 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              13070  1 snd
mac_hid                12681  0 
edac_core              43708  0 
edac_mce_amd           21494  0 
k8temp                 12617  0 
video                  17942  0 
snd_page_alloc         17110  2 snd_hda_intel,snd_pcm
wmi                    17525  0 
shpchp                 35386  0 
lp                     17114  0 
parport                40013  3 parport_pc,ppdev,lp
ums_realtek            17488  0 
usb_storage            44163  2 ums_realtek
uas                    17486  0 
pata_atiixp            12736  0 
r8169                  59719  0 
```
```
dann@dann-laptop:~$ sudo lspci -vnn | grep -A10 VGA
[sudo] password for dann: 
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RS690M [Radeon X1200 Series] [1002:791f] (prog-if 00 [VGA controller])
    Subsystem: Gateway 2000 Device [107b:0381]
    Flags: bus master, fast devsel, latency 64, IRQ 18
    Memory at f0000000 (64-bit, prefetchable) [size=128M]
    Memory at f8100000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at 9000 [size=256]
    Memory at f8000000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [50] Power Management version 2
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit+
    Kernel modules: radeon

```

And here is my /var/log/pm-suspend.log file

```
dann@dann-laptop:~$ cat /var/log/pm-suspend.log
Initial commandline parameters: 
Thu Oct 11 02:51:44 EDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux dann-laptop 3.2.0-23-lowlatency #31-Ubuntu SMP PREEMPT Wed Apr 11 02:24:03 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
arc4                   12458  2 
snd_hda_codec_hdmi     31064  1 
bnep                   17574  2 
rfcomm                 46036  0 
bluetooth             168989  10 bnep,rfcomm
parport_pc             30822  0 
ppdev                  16865  0 
snd_hda_codec_idt      62361  1 
snd_hda_intel          30717  4 
snd_hda_codec          99443  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17255  1 snd_hda_codec
joydev                 17257  0 
uvcvideo               71008  0 
videodev               83376  1 uvcvideo
v4l2_compat_ioctl32    16887  1 videodev
radeon                775556  3 
snd_pcm                84403  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           12848  0 
ttm                    61160  1 radeon
drm_kms_helper         39673  1 radeon
snd_rawmidi            27093  1 snd_seq_midi
r8187se               174868  0 
drm                   200812  5 radeon,ttm,drm_kms_helper
snd_seq_midi_event     13316  1 snd_seq_midi
snd_seq                57369  2 snd_seq_midi,snd_seq_midi_event
snd_timer              27226  2 snd_pcm,snd_seq
snd_seq_device         13175  3 snd_seq_midi,snd_rawmidi,snd_seq
sp5100_tco             12958  0 
snd                    65336  18 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              13070  1 snd
psmouse                78176  0 
serio_raw              12845  0 
video                  17942  0 
mac_hid                12681  0 
edac_core              43708  0 
eeprom_93cx6           12360  1 r8187se
snd_page_alloc         17110  2 snd_hda_intel,snd_pcm
i2c_algo_bit           12902  1 radeon
k8temp                 12617  0 
edac_mce_amd           21494  0 
wmi                    17525  0 
i2c_piix4              12670  0 
shpchp                 35386  0 
lp                     17114  0 
parport                40013  3 parport_pc,ppdev,lp
ums_realtek            17488  0 
usb_storage            44163  1 ums_realtek
uas                    17486  0 
pata_atiixp            12736  0 
r8169                  59719  0 
             total       used       free     shared    buffers     cached
Mem:       3927284    2595744    1331540          0     105952    1938680
-/+ buffers/cache:     551112    3376172
Swap:      3905532          0    3905532

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
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Oct 11 02:51:45 EDT 2012: performing suspend
Initial commandline parameters: 
Thu Oct 11 13:24:43 EDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux dann-laptop 3.2.0-23-lowlatency #31-Ubuntu SMP PREEMPT Wed Apr 11 02:24:03 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
arc4                   12458  2 
bnep                   17574  2 
parport_pc             30822  0 
ppdev                  16865  0 
rfcomm                 46036  0 
bluetooth             168989  10 bnep,rfcomm
snd_hda_codec_hdmi     31064  1 
joydev                 17257  0 
uvcvideo               71008  0 
videodev               83376  1 uvcvideo
v4l2_compat_ioctl32    16887  1 videodev
snd_seq_midi           12848  0 
snd_rawmidi            27093  1 snd_seq_midi
snd_hda_codec_idt      62361  1 
radeon                775556  3 
snd_hda_intel          30717  4 
snd_hda_codec          99443  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17255  1 snd_hda_codec
snd_seq_midi_event     13316  1 snd_seq_midi
snd_pcm                84403  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
edac_core              43708  0 
sp5100_tco             12958  0 
k8temp                 12617  0 
psmouse                78176  0 
serio_raw              12845  0 
edac_mce_amd           21494  0 
i2c_piix4              12670  0 
snd_seq                57369  2 snd_seq_midi,snd_seq_midi_event
ttm                    61160  1 radeon
drm_kms_helper         39673  1 radeon
drm                   200812  5 radeon,ttm,drm_kms_helper
snd_timer              27226  2 snd_pcm,snd_seq
snd_seq_device         13175  3 snd_seq_midi,snd_rawmidi,snd_seq
video                  17942  0 
i2c_algo_bit           12902  1 radeon
snd                    65336  18 snd_hda_codec_hdmi,snd_rawmidi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              13070  1 snd
snd_page_alloc         17110  2 snd_hda_intel,snd_pcm
wmi                    17525  0 
mac_hid                12681  0 
r8187se               174868  0 
shpchp                 35386  0 
eeprom_93cx6           12360  1 r8187se
lp                     17114  0 
parport                40013  3 parport_pc,ppdev,lp
pata_atiixp            12736  0 
r8169                  59719  0 
ums_realtek            17488  0 
uas                    17486  0 
usb_storage            44163  1 ums_realtek
             total       used       free     shared    buffers     cached
Mem:       3927284    1702356    2224928          0      88668    1013260
-/+ buffers/cache:     600428    3326856
Swap:      3905532          0    3905532

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
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Oct 11 13:24:45 EDT 2012: performing suspend
Initial commandline parameters: 
Thu Oct 11 16:36:42 EDT 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux dann-laptop 3.2.0-23-lowlatency #31-Ubuntu SMP PREEMPT Wed Apr 11 02:24:03 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
arc4                   12458  2 
bnep                   17574  2 
rfcomm                 46036  0 
bluetooth             168989  10 bnep,rfcomm
parport_pc             30822  0 
ppdev                  16865  0 
snd_hda_codec_hdmi     31064  1 
joydev                 17257  0 
uvcvideo               71008  0 
videodev               83376  1 uvcvideo
v4l2_compat_ioctl32    16887  1 videodev
snd_hda_codec_idt      62361  1 
snd_seq_midi           12848  0 
snd_hda_intel          30717  4 
snd_hda_codec          99443  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17255  1 snd_hda_codec
radeon                775556  3 
psmouse                78176  0 
snd_pcm                84403  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_rawmidi            27093  1 snd_seq_midi
serio_raw              12845  0 
edac_core              43708  0 
k8temp                 12617  0 
edac_mce_amd           21494  0 
snd_seq_midi_event     13316  1 snd_seq_midi
sp5100_tco             12958  0 
i2c_piix4              12670  0 
snd_seq                57369  2 snd_seq_midi,snd_seq_midi_event
ttm                    61160  1 radeon
drm_kms_helper         39673  1 radeon
r8187se               174868  0 
drm                   200812  5 radeon,ttm,drm_kms_helper
snd_timer              27226  2 snd_pcm,snd_seq
snd_seq_device         13175  3 snd_seq_midi,snd_rawmidi,snd_seq
eeprom_93cx6           12360  1 r8187se
video                  17942  0 
snd                    65336  18 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           12902  1 radeon
soundcore              13070  1 snd
snd_page_alloc         17110  2 snd_hda_intel,snd_pcm
wmi                    17525  0 
shpchp                 35386  0 
mac_hid                12681  0 
lp                     17114  0 
parport                40013  3 parport_pc,ppdev,lp
ums_realtek            17488  0 
usb_storage            44163  1 ums_realtek
uas                    17486  0 
pata_atiixp            12736  0 
r8169                  59719  0 
             total       used       free     shared    buffers     cached
Mem:       3927284    1454128    2473156          0      70584     617396
-/+ buffers/cache:     766148    3161136
Swap:      3905532          0    3905532

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Selected interface 'wlan0'
OK

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Thu Oct 11 16:36:44 EDT 2012: performing hibernate
Initial commandline parameters: 
Thu Oct 11 16:40:11 EDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux dann-laptop 3.2.0-23-lowlatency #31-Ubuntu SMP PREEMPT Wed Apr 11 02:24:03 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
arc4                   12458  2 
snd_hda_codec_hdmi     31064  1 
rfcomm                 46036  0 
bnep                   17574  2 
bluetooth             168989  10 rfcomm,bnep
parport_pc             30822  0 
ppdev                  16865  0 
joydev                 17257  0 
snd_hda_codec_idt      62361  1 
snd_hda_intel          30717  6 
snd_hda_codec          99443  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17255  1 snd_hda_codec
snd_pcm                84403  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uvcvideo               71008  0 
snd_seq_midi           12848  0 
videodev               83376  1 uvcvideo
v4l2_compat_ioctl32    16887  1 videodev
snd_rawmidi            27093  1 snd_seq_midi
snd_seq_midi_event     13316  1 snd_seq_midi
snd_seq                57369  2 snd_seq_midi,snd_seq_midi_event
radeon                775556  2 
snd_timer              27226  2 snd_pcm,snd_seq
snd_seq_device         13175  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                78176  0 
edac_core              43708  0 
serio_raw              12845  0 
edac_mce_amd           21494  0 
sp5100_tco             12958  0 
snd                    65336  22 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k8temp                 12617  0 
i2c_piix4              12670  0 
ttm                    61160  1 radeon
drm_kms_helper         39673  1 radeon
drm                   200812  4 radeon,ttm,drm_kms_helper
video                  17942  0 
soundcore              13070  1 snd
snd_page_alloc         17110  2 snd_hda_intel,snd_pcm
i2c_algo_bit           12902  1 radeon
wmi                    17525  0 
mac_hid                12681  0 
r8187se               174868  0 
eeprom_93cx6           12360  1 r8187se
shpchp                 35386  0 
lp                     17114  0 
parport                40013  3 parport_pc,ppdev,lp
ums_realtek            17488  0 
usb_storage            44163  1 ums_realtek
uas                    17486  0 
pata_atiixp            12736  0 
r8169                  59719  0 
             total       used       free     shared    buffers     cached
Mem:       3927284     648372    3278912          0      61664     293064
-/+ buffers/cache:     293644    3633640
Swap:      3905532          0    3905532

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
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Oct 11 16:40:13 EDT 2012: performing suspend
Initial commandline parameters: 
Thu Oct 11 16:58:44 EDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux dann-laptop 3.2.0-23-lowlatency #31-Ubuntu SMP PREEMPT Wed Apr 11 02:24:03 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
btrfs                 632603  0 
zlib_deflate           25725  1 btrfs
libcrc32c              12426  1 btrfs
ufs                    73994  0 
qnx4                   17398  0 
hfsplus                83863  0 
hfs                    53950  0 
minix                  35645  0 
ntfs                   98239  0 
vfat                   17259  0 
msdos                  17046  0 
fat                    57785  2 vfat,msdos
jfs                   178715  0 
xfs                   761976  0 
reiserfs              237368  0 
ext2                   71675  0 
arc4                   12458  2 
snd_hda_codec_hdmi     31064  1 
rfcomm                 46036  0 
bnep                   17574  2 
parport_pc             30822  0 
bluetooth             168989  10 rfcomm,bnep
ppdev                  16865  0 
joydev                 17257  0 
uvcvideo               71008  0 
videodev               83376  1 uvcvideo
v4l2_compat_ioctl32    16887  1 videodev
snd_hda_codec_idt      62361  1 
snd_seq_midi           12848  0 
snd_rawmidi            27093  1 snd_seq_midi
snd_seq_midi_event     13316  1 snd_seq_midi
snd_seq                57369  2 snd_seq_midi,snd_seq_midi_event
snd_hda_intel          30717  4 
snd_hda_codec          99443  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17255  1 snd_hda_codec
snd_pcm                84403  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
radeon                775556  3 
psmouse                78176  0 
snd_seq_device         13175  3 snd_seq_midi,snd_rawmidi,snd_seq
edac_core              43708  0 
edac_mce_amd           21494  0 
k8temp                 12617  0 
serio_raw              12845  0 
snd_timer              27226  2 snd_seq,snd_pcm
sp5100_tco             12958  0 
i2c_piix4              12670  0 
snd                    65336  18 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_rawmidi,snd_seq,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_device,snd_timer
ttm                    61160  1 radeon
drm_kms_helper         39673  1 radeon
drm                   200812  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           12902  1 radeon
soundcore              13070  1 snd
snd_page_alloc         17110  2 snd_hda_intel,snd_pcm
video                  17942  0 
wmi                    17525  0 
mac_hid                12681  0 
r8187se               174868  0 
shpchp                 35386  0 
eeprom_93cx6           12360  1 r8187se
lp                     17114  0 
parport                40013  3 parport_pc,ppdev,lp
ums_realtek            17488  0 
uas                    17486  0 
usb_storage            44163  1 ums_realtek
pata_atiixp            12736  0 
r8169                  59719  0 
             total       used       free     shared    buffers     cached
Mem:       3927284    1126556    2800728          0      57356     468036
-/+ buffers/cache:     601164    3326120
Swap:      3905532          0    3905532

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
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Oct 11 16:58:46 EDT 2012: performing suspend
Initial commandline parameters: 
Thu Oct 11 17:14:06 EDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux dann-laptop 3.2.0-23-lowlatency #31-Ubuntu SMP PREEMPT Wed Apr 11 02:24:03 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
arc4                   12458  2 
snd_hda_codec_hdmi     31064  1 
bnep                   17574  2 
rfcomm                 46036  0 
bluetooth             168989  10 bnep,rfcomm
parport_pc             30822  0 
ppdev                  16865  0 
joydev                 17257  0 
uvcvideo               71008  0 
videodev               83376  1 uvcvideo
v4l2_compat_ioctl32    16887  1 videodev
snd_hda_codec_idt      62361  1 
snd_hda_intel          30717  4 
snd_hda_codec          99443  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17255  1 snd_hda_codec
snd_seq_midi           12848  0 
snd_pcm                84403  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_rawmidi            27093  1 snd_seq_midi
psmouse                78176  0 
snd_seq_midi_event     13316  1 snd_seq_midi
serio_raw              12845  0 
k8temp                 12617  0 
sp5100_tco             12958  0 
edac_core              43708  0 
edac_mce_amd           21494  0 
i2c_piix4              12670  0 
snd_seq                57369  2 snd_seq_midi,snd_seq_midi_event
snd_timer              27226  2 snd_pcm,snd_seq
snd_seq_device         13175  3 snd_seq_midi,snd_rawmidi,snd_seq
video                  17942  0 
radeon                775556  3 
ttm                    61160  1 radeon
drm_kms_helper         39673  1 radeon
snd                    65336  18 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   200812  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           12902  1 radeon
soundcore              13070  1 snd
snd_page_alloc         17110  2 snd_hda_intel,snd_pcm
r8187se               174868  0 
wmi                    17525  0 
eeprom_93cx6           12360  1 r8187se
mac_hid                12681  0 
shpchp                 35386  0 
lp                     17114  0 
parport                40013  3 parport_pc,ppdev,lp
pata_atiixp            12736  0 
r8169                  59719  0 
ums_realtek            17488  0 
uas                    17486  0 
usb_storage            44163  1 ums_realtek
             total       used       free     shared    buffers     cached
Mem:       3927284     846944    3080340          0      50432     318608
-/+ buffers/cache:     477904    3449380
Swap:      3905532          0    3905532

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
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Oct 11 17:14:08 EDT 2012: performing suspend
Initial commandline parameters: 
Thu Oct 11 17:25:33 EDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux dann-laptop 3.2.0-23-lowlatency #31-Ubuntu SMP PREEMPT Wed Apr 11 02:24:03 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
arc4                   12458  2 
snd_hda_codec_hdmi     31064  1 
bnep                   17574  2 
rfcomm                 46036  0 
bluetooth             168989  10 bnep,rfcomm
parport_pc             30822  0 
ppdev                  16865  0 
joydev                 17257  0 
ums_realtek            17488  0 
uas                    17486  0 
snd_hda_codec_idt      62361  1 
snd_seq_midi           12848  0 
uvcvideo               71008  0 
videodev               83376  1 uvcvideo
snd_hda_intel          30717  4 
snd_hda_codec          99443  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
v4l2_compat_ioctl32    16887  1 videodev
snd_hwdep              17255  1 snd_hda_codec
snd_rawmidi            27093  1 snd_seq_midi
pata_atiixp            12736  0 
snd_pcm                84403  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
edac_core              43708  0 
snd_seq_midi_event     13316  1 snd_seq_midi
k8temp                 12617  0 
edac_mce_amd           21494  0 
psmouse                78176  0 
serio_raw              12845  0 
sp5100_tco             12958  0 
i2c_piix4              12670  0 
snd_seq                57369  2 snd_seq_midi,snd_seq_midi_event
radeon                775556  3 
video                  17942  0 
snd_timer              27226  2 snd_pcm,snd_seq
snd_seq_device         13175  3 snd_seq_midi,snd_rawmidi,snd_seq
r8169                  59719  0 
ttm                    61160  1 radeon
drm_kms_helper         39673  1 radeon
drm                   200812  5 radeon,ttm,drm_kms_helper
snd                    65336  18 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           12902  1 radeon
soundcore              13070  1 snd
snd_page_alloc         17110  2 snd_hda_intel,snd_pcm
r8187se               174868  0 
wmi                    17525  0 
mac_hid                12681  0 
eeprom_93cx6           12360  1 r8187se
shpchp                 35386  0 
lp                     17114  0 
parport                40013  3 parport_pc,ppdev,lp
usb_storage            44163  1 ums_realtek
             total       used       free     shared    buffers     cached
Mem:       3927284    1180908    2746376          0      54176     442912
-/+ buffers/cache:     683820    3243464
Swap:      3905532          0    3905532

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
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Oct 11 17:25:35 EDT 2012: performing suspend

```

---

### Post by Toz on 2012-10-11
I've created a new thread for this issue - the other one was getting crowded with different issues.

I notice that you are running a low-latency kernel. Have you tried suspending with the regular kernel?

Also, have a look at this link ([https://wiki.ubuntu.com/DebuggingKernelSuspend]("https://wiki.ubuntu.com/DebuggingKernelSuspend")) for information on how to debug a suspend/resume issue.

---

