---
title: "Multiple audio cards, which modules to disable?"
date: 2008-05-29
forum: Hardware
---

### Post by scfamily on 2008-05-29
Hello folks.

I am trying to disable the modules loading for 2 out of 3 audio cards currently on my system.

I'm running a dual boot Ubuntu 8.04 64bit/ WinXp system. Both OS's have their own hard drive.

I did not mean to have 3 cards, just ended up that way..:guitar:

The mobo is a Gigabyte GA-MA69G-S3H with integrated ALC889A audio.

My vid card is a ATI HD 2600xt with built in sound for the HDMI output.

Finally I tossed in my trusty SB Live EMU10K1 for good measure, as I have read that any other audio card than a EMU10K1 will cause applications to fight for the card.

The dilemma I face -

I cannot disable the onboard audio in the bios as the wife would kill me. The way I have XP setup, the onboard audio is attached to the stereo system for her Itunes.I use the soundblaster for my headphones with games on XP.

I cannot disable the built in audio of the vid card.

I would like to blacklist the modules for the other cards other than the SB Live.

A lsmod in terminal has the following entries.
```
Module                  Size  Used by
ipv6                  311720  14 
binfmt_misc            14860  1 
af_packet              27272  2 
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67748  4 rfcomm,l2cap
ppdev                  11400  0 
powernow_k8            16608  1 
cpufreq_powersave       3200  0 
cpufreq_ondemand       11152  1 
cpufreq_stats           8416  0 
freq_table              6464  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative    10632  0 
cpufreq_userspace       6180  0 
video                  23444  0 
output                  5632  1 video
dock                   12960  0 
container               6656  0 
sbs                    17808  0 
sbshc                   8960  1 sbs
battery                16776  0 
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
ac                      8328  0 
sbp2                   27272  0 
lp                     14916  0 
snd_emu10k1_synth       9472  0 
snd_emux_synth         40960  1 snd_emu10k1_synth
snd_seq_virmidi         9344  1 snd_emux_synth
snd_seq_midi_emul       9088  1 snd_emux_synth
snd_emu10k1           162272  4 snd_emu10k1_synth
snd_ac97_codec        123224  1 snd_emu10k1
snd_seq_dummy           5764  0 
ac97_bus                3840  1 snd_ac97_codec
snd_hda_intel         440408  2 
joydev                 15488  0 
snd_seq_oss            38912  0 
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
snd_seq_midi           10688  0 
fglrx                1804800  27 
usblp                  17664  0 
snd_rawmidi            29856  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_pcm                92168  4 snd_emu10k1,snd_ac97_codec,snd_hda_intel,snd_pcm_oss
snd_seq_midi_event     10112  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
emu10k1_gp              5632  0 
snd_page_alloc         13200  3 snd_emu10k1,snd_hda_intel,snd_pcm
snd_util_mem            6656  2 snd_emux_synth,snd_emu10k1
gameport               17936  2 emu10k1_gp
snd_seq                63232  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_hwdep              12552  3 snd_emux_synth,snd_emu10k1,snd_hda_intel
snd_timer              27912  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         10644  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_piix4              11148  0 
psmouse                46236  0 
snd                    70856  25 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_seq_dummy,snd_hda_intel,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_hwdep,snd_timer,snd_seq_device
i2c_core               28544  1 i2c_piix4
serio_raw               9092  0 
button                 10912  0 
k8temp                  7680  0 
parport_pc             41128  1 
parport                44300  3 ppdev,lp,parport_pc
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
soundcore              10400  1 snd
evdev                  14976  4 
pcspkr                  4992  0 
usb_storage            82496  0 
ext3                  149264  1 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
ide_disk               19072  3 
ide_cd                 35488  0 
cdrom                  41512  1 ide_cd
ata_generic             9988  0 
pata_acpi               9856  0 
pata_atiixp            10496  0 
libusual               23520  1 usb_storage
usbhid                 35168  0 
hid                    44992  1 usbhid
sg                     41880  0 
sd_mod                 33280  0 
floppy                 69096  0 
ohci1394               36532  0 
r8169                  36612  0 
ieee1394              106968  2 sbp2,ohci1394
atiixp                  6672  0 [permanent]
ide_core              136600  3 ide_disk,ide_cd,atiixp
ehci_hcd               41996  0 
ohci_hcd               27524  0 
ahci                   33028  0 
usbcore               169904  7 usblp,usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd
libata                176304  4 ata_generic,pata_acpi,pata_atiixp,ahci
scsi_mod              178488  5 sbp2,usb_storage,sg,sd_mod,libata
thermal                19744  0 
processor              41448  2 powernow_k8,thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  3 

```

If anyone could point out what modules I can blacklist so only the SB live is loaded, I would very much appreciate it.

My current assumption is anything audio-wise without 10k in the last header is what i need to blacklist, but want to be sure.

Also what format should the blacklist be in would be a great help.

Thank you for your time.

Steve

---

