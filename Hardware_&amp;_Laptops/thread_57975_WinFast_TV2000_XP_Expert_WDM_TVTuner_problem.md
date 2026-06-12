---
title: "WinFast TV2000 XP Expert WDM TVTuner problem"
date: 2005-08-18
forum: Hardware &amp; Laptops
---

### Post by Matthai on 2005-08-18
I have WinFast TV2000 XP Expert WDM TVTuner under Kubuntu 5.04.
I am using ktv for viewing TV. BTW: teletext is not working, but here is other problem.

The picture is OK, but there is no sound.

I have been searching for a solution on the forum, and found that there should be added a file with the line: "options bttv card=34 tuner=2" in the directory /etc/modprobe.d.

But there is no information about how that file should be named.

ls -l of /etc/modprobe.d is:
-rw-r--r--  1 root root  4745 2005-01-14 14:38 aliases
-rw-r--r--  1 root root 11691 2005-03-25 23:08 alsa-base
drwxr-xr-x  2 root root  4096 2005-07-12 10:58 arch
lrwxrwxrwx  1 root root     9 2005-07-12 10:58 arch-aliases -> arch/i386
-rw-r--r--  1 root root    38 2005-04-01 14:37 ibm_acpi.modprobe
drwxr-xr-x  2 root root  4096 2005-07-12 10:58 isapnp
-rw-r--r--  1 root root    29 2005-04-05 00:40 nvidia-kernel-nkc
-rw-r--r--  1 root root    41 2005-04-01 14:37 toshiba_acpi.modprobe

In which file should I add that line?

BTW, lsmod gives the following output, I can't find bttv:
Module                  Size  Used by
radeon                 69760  1
drm                    59412  2 radeon
ipv6                  229504  8
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
e100                   32384  0
mii                     4736  1 e100
ohci1394               31876  0
tda9887                13208  0
tuner                  20388  0
cx8800                 29196  0
cx88xx                 46868  1 cx8800
i2c_algo_bit            9224  1 cx88xx
video_buf              20484  2 cx8800,cx88xx
v4l1_compat            13572  1 cx8800
v4l2_common             5888  1 cx8800
btcx_risc               4744  2 cx8800,cx88xx
videodev                9728  2 cx8800,cx88xx
snd_intel8x0           29984  2
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  9 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
i2c_i801                8076  0
i2c_core               21264  5 tda9887,tuner,cx88xx,i2c_algo_bit,i2c_i801
uhci_hcd               30224  0
usbcore               107384  2 uhci_hcd
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
intel_mch_agp          10000  0
intel_agp              20636  1
agpgart                31784  3 drm,intel_mch_agp,intel_agp
analog                 10784  0
gameport                4608  1 analog
floppy                 54864  0
pcspkr                  3816  0
rtc                    12216  0
md                     43856  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
evdev                   9088  0
tsdev                   7488  0
sr_mod                 16036  0
sbp2                   22408  0
scsi_mod              119936  2 sr_mod,sbp2
ieee1394              100408  2 ohci1394,sbp2
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  2 sr_mod,ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
piix                    9988  1
ide_disk               18176  4
ide_core              118988  4 ide_cd,ide_generic,piix,ide_disk
unix                   26164  460
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

And dmesg gives the following listing:
UTO_STEREO
cx88[0]/0: AUD_STATUS: 0x4172 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x4232 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x41b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x41f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x42b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x4332 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x43b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x4432 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x44f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x45f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x47b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x48b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x49f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x49b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x4ab2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x4bb2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x4c32 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x4c72 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x4d72 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x4db2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x4e32 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x4f72 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x5072 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x5032 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x50b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x51b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x52f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x53b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x5532 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x56b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x5772 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x5732 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x5872 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x5832 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x5872 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x58b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x59f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x5a72 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x5af2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x5c32 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x5c72 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x5c32 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x5cf2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x5d32 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x5cf2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x5c72 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x5cf2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x5d72 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x5e32 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x5ef2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x5fb2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x6132 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x6232 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x62f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x6432 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x6532 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x64b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x6432 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x64b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x65b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x6672 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x66b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x6672 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x6572 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x65f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x66b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x6672 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x66f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x67f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x6832 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x68f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x6a32 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x6b32 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x6c32 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x6db2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x6eb2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x6f72 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x6f32 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x6ef2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x6e32 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x6f72 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x6fb2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x6ff2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x7032 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x7132 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x71f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x7172 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x71f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x7232 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x7272 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x7372 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x7432 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x7532 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x74f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x75f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x76f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x7732 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x7772 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x77b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x78f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x7b32 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x7c32 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x7cf2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x7d32 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x7c72 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x7d72 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x7db2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x7f32 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x7f72 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x8132 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x83b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x8532 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x8672 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x87f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x88f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x8a32 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x8b72 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x8c32 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x8d32 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x8f72 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x9172 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x9372 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x9572 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x9632 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x9732 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x9932 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x99f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x9cf2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x9db2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x9f32 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xa032 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xa172 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xa3f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xa572 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xa772 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xa8f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xa9f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xabb2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xad32 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xaeb2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xaef2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xafb2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xb032 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xb1b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xb172 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xb372 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xb4f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xb532 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xb6f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xb7b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xb8f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xba72 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xbbb2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xbcb2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xbdf2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xbeb2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xbef2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xbff2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xc1b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xc232 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xc3b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xc4b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xc5b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xc672 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xc772 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xc7f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xc8f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xca32 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xcaf2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xccb2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xcdb2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xcfb2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xd072 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xd232 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xd432 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xd5f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xd632 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xd672 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xd7b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xd872 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xd932 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xd972 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xdab2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xdaf2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xdc72 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xddb2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xddf2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xde32 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xdf32 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xdef2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xdf72 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xe032 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xe172 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xe232 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xe272 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xe3b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xe3f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xe572 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xe4f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xe5b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xe632 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xe6f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xe732 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xe772 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xe8f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xe9b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xeab2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xeb32 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xec32 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xecf2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xedf2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xef32 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xeff2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xf172 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xf2f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xf232 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xf332 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xf3f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xf572 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xf632 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xf772 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xf7b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xf9f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xfb72 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xfbf2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xfc72 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xfe32 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0xff72 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x72 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x1f2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x2b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x372 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x532 [mono/no pilot] ctl=BTSC_AUTO_STEREO
cx88[0]/0: AUD_STATUS: 0x6b2 [mono/no pilot] ctl=BTSC_AUTO_STEREO


BTW: captured picture (if captured in jpeg file by ktv) is of very, very low quality. However capturing picture under Windows works fine. Which program you suggest for capturing video (MPEG4 or xvid for instance) from TV Tuner?
What about teletext?

---

### Post by c-m on 2005-08-18
Hi, I have a Hauppauge WinTV-GO car, which everyone says works easily under linux. Well i have a similar problem to you in that i have a good picture but the only sound i get is static or white noise.

I have searched everywhere and everything on the internet in order to fix this.

Now an lspci shows my card as:

> 
0000:01:07.0 Multimedia video controller: Conexant Winfast TV2000 XP (rev 05)
0000:01:07.1 Multimedia controller: Conexant: Unknown device 8811 (rev 05)


Looking at the chip on my card shows that uses a conexant CX2388 chip. now from what i've found on the internet is that while the 2.6.10 kenel does have drivers for this, they are quite poor version 0.01, i think version 0.03 or 4 is out. Even then the FAQ mentions that some people have experienced difficulties in gaining any sound from the device and at present there is no fix.

If you know any more, or eventually sort out the sound on yours please let me know.

cheers.

---

### Post by Matthai on 2005-08-19
my lspci prints this:

0000:02:00.0 Multimedia video controller: Conexant Winfast TV2000 XP (rev 05)
0000:02:04.0 Communication controller: Conexant: Unknown device 2f11 (rev 01)

---

### Post by mctavish on 2005-08-19
I have one of these winfast xp expert thingys.

Mine came with a cable that connected the card to my soundcard. Have you done that? 

I plugged the cable from the winfast card into the auxiliary input on my soundblaster, then I had to make sure the aux channel volume was up, and it worked fine.

---

