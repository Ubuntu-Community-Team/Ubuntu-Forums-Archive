---
title: "standby (suspend-to-ram) doesn't work"
date: 2008-04-27
forum: Hardware
---

### Post by niobos on 2008-04-27
I'm trying to get my Desktop PC into standby (aka suspend-to-ram) but, as the subject line already said, it doesn't work.

I'm sure that the hardware is OK and is supported, because my Gentoo-kernel (2.6.22) will suspend and resume just fine.

when I manually try to "echo mem > /sys/power/state" from the console (X not running for testing purposes) the machine hangs. The console keeps its contents, no HDD-spindown, ... it just freezes. The only solution is a hard power-down (5 seconds power-button is enough, no need to cut the AC)

Can anyone give me some clues where to start?

Some info that might be useful; if I missed something, feel free to ask
```
# uname -a
Linux bigbrother 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
# cat /proc/acpi/info
version:                 20070126
# lsmod
Module                  Size  Used by
rfcomm                 42136  2
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
nfsd                  220912  13
exportfs                7040  1 nfsd
fglrx                 656352  15
ppdev                  10244  0
speedstep_lib           6404  0
cpufreq_powersave       2688  0
cpufreq_stats           7232  0
cpufreq_userspace       5280  0
cpufreq_ondemand        9612  0
cpufreq_conservative     8072  0
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
video                  18060  0
container               5504  0
sbs                    19592  0
button                  8976  0
dock                   10656  0
ac                      6148  0
battery                11012  0
ipv6                  273892  10
nfs                   246124  3
lockd                  67592  3 nfsd,nfs
sunrpc                172412  10 nfsd,nfs,lockd
ext2                   67208  1
mbcache                 9732  1 ext2
sbp2                   24072  0
lp                     12580  0
loop                   19076  0
snd_intel8x0           34972  1
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
saa7134_alsa           15392  1
snd_pcm_oss            44672  0
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  4 snd_intel8x0,snd_ac97_codec,saa7134_alsa,snd_pcm_oss
saa7134_dvb            18188  0
dvb_pll                15492  1 saa7134_dvb
video_buf_dvb           7812  1 saa7134_dvb
dvb_core               82216  1 video_buf_dvb
tda1004x               17028  1 saa7134_dvb
snd_mpu401              9640  0
snd_mpu401_uart         9600  1 snd_mpu401
snd_seq_dummy           4740  0
snd_seq_oss            33152  0
snd_seq_midi            9600  0
tuner                  63144  0
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
saa7134               129100  2 saa7134_alsa,saa7134_dvb
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
video_buf              26244  4 saa7134_alsa,saa7134_dvb,video_buf_dvb,saa7134
compat_ioctl32          2304  1 saa7134
ir_kbd_i2c              9872  1 saa7134
i2c_core               26112  6 saa7134_dvb,dvb_pll,tda1004x,tuner,saa7134,ir_kbd_i2c
xpad                    9988  0
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  17 snd_intel8x0,snd_ac97_codec,saa7134_alsa,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ir_common              35460  2 saa7134,ir_kbd_i2c
videodev               29312  1 saa7134
v4l2_common            18432  3 tuner,saa7134,videodev
v4l1_compat            15364  2 saa7134,videodev
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
soundcore               8800  1 snd
af_packet              24840  2
iTCO_wdt               11940  0
iTCO_vendor_support     4868  1 iTCO_wdt
parport_pc             37412  1
parport                37448  3 ppdev,lp,parport_pc
pcspkr                  4224  0
psmouse                39952  0
serio_raw               8068  0
shpchp                 34580  0
pci_hotplug            32704  1 shpchp
intel_agp              25620  1
agpgart                35016  2 fglrx,intel_agp
evdev                  11136  6
usb_storage            73024  0
ide_core              116804  1 usb_storage
reiserfs              248704  1
sg                     36764  0
sr_mod                 17828  0
cdrom                  37536  1 sr_mod
sd_mod                 30336  3
libusual               18448  1 usb_storage
usbhid                 29536  0
hid                    28928  1 usbhid
ata_piix               17540  2
ohci1394               36528  0
ieee1394               96312  2 sbp2,ohci1394
floppy                 60004  0
via_rhine              25992  0
mii                     6528  1 via_rhine
ata_generic             8452  0
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  6 sbp2,usb_storage,sg,sr_mod,sd_mod,libata
ehci_hcd               36492  0
uhci_hcd               26640  0
usbcore               138632  7 xpad,usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
dm_mirror              24448  0
dm_snapshot            18980  0
dm_mod                 58816  10 dm_mirror,dm_snapshot
thermal                14344  1
processor              32072  1 thermal
fan                     5764  1
fuse                   47124  1
apparmor               40728  0
commoncap               8320  1 apparmor

```

---

### Post by niobos on 2008-04-27
I managed to narrow the problem down to an fglrx-incompatibility. When I quit X and rmmod fglrx suspend/resume works fine.
As soon as I modprobe fglrx, suspend breaks.

Google tells me I'm not the only one with this problem, although some "workarounds" date from 2005

---

### Post by jf.jouvet on 2008-05-26
Hi 
with ubuntu 8.04, on a laptop lenovo 3000 n200, I did what Bighadded said in alsa-base file, (options snd-hda_intel model=lenovo) but without success; still no sound, (with XP i have sound (dual boot laptop))
I tried to add in the same line 'index = 0' just before 'model=lenovo' and restart, and then sound icon was set to not active
So i remove index=0 and Sound icon is set to active, but no sound
(I tried with totem and vlc)

before , with ubuntu 7.04, I did the same modification with success but with 8.04 no

Any idea?
thanks in advance

---

### Post by niobos on 2008-05-26
just to reply to myself:
[http://blog.vaxius.net/?tag=slub](http://blog.vaxius.net/?tag=slub)

---

