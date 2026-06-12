---
title: "No sound, at all..."
date: 2004-12-11
forum: Hardware &amp; Laptops
---

### Post by niobe_logos on 2004-12-11
Hello, all:

I installed Ubuntu as a replacement for Fedora Core 2 and really like it. The whole install process is really smooth, and everything works like a charm...except for sound. I had sound until the first Synaptic upgrade, and then never again. I've read a bunch of documentation, and tried a bunch of stuff, and I'm a Linux newbie, and at my wits' end.  I have a Creative Live! soundcard, nVidia AGP graphics card, Asus A7V600 mobo with Athlon XP. 

Here's lspci:

nyondo@nadibeast:~ $ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0a.0 Communication controller: Conexant: Unknown device 1085 (rev 08)
0000:00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [K8T800 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:00:13.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
0000:00:13.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV10 [GeForce 256 SDR] (rev 10)

and lsmod:

nyondo@nadibeast:~ $ lsmod
Module                  Size  Used by
sound                  75308  0
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
button                  6936  0
ac                      5132  0
battery                 9740  0
ipv6                  230020  8
emu10k1_gp              3840  0
snd_emu10k1            80776  5
snd_util_mem            4608  1 snd_emu10k1
snd_hwdep               9120  1 snd_emu10k1
via_rhine              19848  0
mii                     4864  1 via_rhine
crc32                   4608  1 via_rhine
snd_via82xx            26660  2
snd_ac97_codec         59268  2 snd_emu10k1,snd_via82xx
snd_pcm_oss            48168  0
snd_mixer_oss          16640  4 snd_pcm_oss
snd_pcm                85540  4 snd_emu10k1,snd_via82xx,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd_page_alloc         11144  3 snd_emu10k1,snd_via82xx,snd_pcm
snd_mpu401_uart         7296  1 snd_via82xx
snd_rawmidi            23232  2 snd_emu10k1,snd_mpu401_uart
snd_seq_device          7944  2 snd_emu10k1,snd_rawmidi
snd                    50660  19 snd_emu10k1,snd_util_mem,snd_hwdep,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  5 sound,snd
ehci_hcd               27780  0
uhci_hcd               29328  0
usbcore               104292  4 ehci_hcd,uhci_hcd
sata_via                7428  0
libata                 36356  1 sata_via
scsi_mod              115148  1 libata
via_agp                 8832  1
agpgart                31784  2 via_agp
pcspkr                  3816  0
rtc                    12216  0
analog                 10784  0
gameport                4736  3 emu10k1_gp,snd_via82xx,analog
floppy                 54996  0
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
nvidia               4821428  12
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
tsdev                   7168  0
evdev                   9088  0
ide_cd                 38276  1
cdrom                  35872  1 ide_cd
mousedev               10124  1
psmouse                17800  0
ext3                  109544  2
jbd                    54552  1 ext3
ide_generic             1664  0
via82cxxx              13084  1
ide_disk               16768  5
ide_core              125272  4 ide_cd,ide_generic,via82cxxx,ide_disk
unix                   25904  648
fan                     4236  0
thermal                13200  0
processor              17712  1 thermal
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb

I have played with all the mixer sliders and gotten nothing except a few crackles or pops. I do not have alsaconf. I tried upgrading ALSA drivers, but when I use a shell to install, config complains I already have ALSA installed (true, version 1.0.4). I tried upgrading via hoary to 1.0.7, but I still get this:

nyondo@nadibeast:~ $ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.4 (Mon May 17 14:31:44 2004 UTC).
Compiled on Nov 18 2004 for kernel 2.6.8.1-3-386.

How can I upgrade the Alsa drivers? I'm still a Linux newbie, and need a good guide to upgrading modules...

I also tried installing the nvidia audio drivers (NFORCE) but nvmixer gives me this:

nvmixer: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

I'm outta clues! Any and all help would be appreciated...

---

### Post by taygan on 2004-12-11
Hmmm. I've got the ASUS A7V600-X with an Athlon XP and although it's a bit crackly at the high end, system sounds work fine..  There is hope that the VIA 8237 will be fully supported in kernel 2.10, as it's running off the Via82xx drivers that aren't an exact fit (they're for up to 8235 I believe)

here's my lsmod for comparsion:
Module                  Size  Used by
proc_intf               3840  0
freq_table              4292  0
cpufreq_userspace       5336  0
cpufreq_powersave       1792  0
button                  6680  0
ac                      4876  0
battery                 9484  0
af_packet              22344  2
via_rhine              21320  0
mii                     5120  1 via_rhine
crc32                   4352  1 via_rhine
snd_via82xx            29028  4
snd_ac97_codec         67908  1 snd_via82xx
snd_pcm_oss            53160  0
snd_mixer_oss          19520  3 snd_pcm_oss
snd_pcm                95332  3 snd_via82xx,snd_pcm_oss
snd_timer              25028  1 snd_pcm
snd_page_alloc         11528  2 snd_via82xx,snd_pcm
snd_mpu401_uart         7872  1 snd_via82xx
snd_rawmidi            25088  1 snd_mpu401_uart
snd_seq_device          8136  1 snd_rawmidi
snd                    55524  12 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10208  3 snd
ehci_hcd               30852  0
uhci_hcd               32208  0
usbcore               115876  4 ehci_hcd,uhci_hcd
via82cxxx              13916  1
via_agp                 9024  1
agpgart                33704  1 via_agp
pcspkr                  3688  0
rtc                    12600  0
analog                 11808  0
gameport                4672  2 snd_via82xx,analog
floppy                 59348  0
nls_iso8859_1           4096  1
nls_cp437               5760  1
vfat                   14592  1
fat                    46144  1 vfat
md                     48648  0
dm_mod                 57660  1
capability              4616  0
commoncap               7168  1 capability
nvidia               4821492  12
parport_pc             34944  1
lp                     10820  0
parport                40904  2 parport_pc,lp
ide_generic             1472  0
ide_disk               18816  0
tsdev                   7296  0
evdev                   9536  0
ide_cd                 41732  0
ide_core              136344  4 via82cxxx,ide_generic,ide_disk,ide_cd
cdrom                  39648  1 ide_cd
mousedev               10316  1
psmouse                19784  0
ext3                  124712  2
jbd                    61144  1 ext3
mbcache                 9156  1 ext3
sd_mod                 21440  5
sata_via                7492  9
libata                 40516  1 sata_via
scsi_mod              122828  2 sd_mod,libata
unix                   28272  671
fan                     4044  0
thermal                13072  0
processor              17456  1 thermal
font                    8448  0
vesafb                  6624  0
cfbcopyarea             3776  1 vesafb
cfbimgblt               3136  1 vesafb
cfbfillrect             3712  1 vesafb

You've tried the alsamixer from the command line I assume?

---

### Post by niobe_logos on 2004-12-11
Yes, I did. I just tried it again, and for a wonder, it worked! Now everthing has sound.

Frustrating though...I have no idea **what** worked, or what to tell folks with a similar problem. For the last *day* I've been pushing at sliders and installing and reinstalling things. I'll keep an eye on things, see if the sound stays, or gives up with the next reboot.

One thing I've heard is that I shouldn't upgrade the kernel to 2.6.9, because nVidia hasn't cobbled together any drivers that work with it yet. So no auto-upgrades through Synaptic, for a while.

---

### Post by niobe_logos on 2004-12-11
Update: so far, so good. Everything seems to work, except for XMMS controls.

---

