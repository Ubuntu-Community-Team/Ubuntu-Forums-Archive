---
title: "DMA for IDE doesn't work in hardy on nvidia2"
date: 2008-04-21
forum: Hardware &amp; Laptops
---

### Post by tlknv on 2008-04-21
Hi All,
I installed hardy( betta ) several days ago and upgrated the kernel to the current version 2.6.24-16-generic. Now I'm unable to turn DMA on for my IDE HDD ( and IDE DVD as well ). sudo hdparm -d1 /dev/hda shows a message about insufficient permission. Please note: this kernel doesn't have amd74xx. I tried to reorder (ata|ide) modules in /etc/initramfs-tools/modules in several ways. No luck.

Here is my lsmod with untouched /etc/initramfs-tools/modules
Module Size Used by
isofs 36388 1
udf 88612 0
ipv6 267780 8
af_packet 23812 2
rfcomm 41744 2
l2cap 25728 13 rfcomm
bluetooth 61156 4 rfcomm,l2cap
ppdev 10372 0
cpufreq_powersave 2688 0
cpufreq_stats 7104 0
cpufreq_userspace 5284 0
cpufreq_ondemand 9740 0
cpufreq_conservative 8712 0
freq_table 5536 2 cpufreq_stats,cpufreq_ondemand
video 19856 0
output 4736 1 video
container 5632 0
sbs 15112 0
sbshc 7680 1 sbs
dock 11280 0
battery 14212 0
iptable_filter 3840 0
ip_tables 14820 1 iptable_filter
x_tables 16132 1 ip_tables
ext3 136712 1
jbd 48404 1 ext3
mbcache 9600 1 ext3
ac 6916 0
sbp2 24072 0
lp 12324 0
snd_mpu401 9448 0
snd_mpu401_uart 9728 1 snd_mpu401
evdev 13056 3
analog 13600 0
gameport 16008 1 analog
snd_intel8x0 35356 3
snd_ac97_codec 101028 1 snd_intel8x0
ac97_bus 3072 1 snd_ac97_codec
snd_pcm_oss 42144 0
snd_mixer_oss 17920 1 snd_pcm_oss
snd_pcm 78596 3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy 4868 0
parport_pc 36260 1
parport 37832 3 ppdev,lp,parport_pc
serio_raw 7940 0
button 9232 0
snd_seq_oss 35584 0
psmouse 40336 0
snd_seq_midi 9376 0
snd_rawmidi 25760 2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event 8320 2 snd_seq_oss,snd_seq_midi
snd_seq 54224 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer 24836 2 snd_pcm,snd_seq
snd_seq_device 9612 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_nforce2 7680 0
i2c_core 24832 1 i2c_nforce2
nvidia_agp 9628 1
shpchp 34452 0
pci_hotplug 30880 1 shpchp
agpgart 34760 1 nvidia_agp
snd 56996 19 snd_mpu401,snd_mpu401_uart,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore 8800 1 snd
snd_page_alloc 11400 2 snd_intel8x0,snd_pcm
pcspkr 4224 0
reiserfs 239616 3
ide_cd 32544 1
cdrom 37408 1 ide_cd
ide_disk 17536 6
ata_generic 8324 0
pata_amd 14212 0
floppy 59588 0
ohci1394 33584 0
pata_acpi 8320 0
ieee1394 93752 2 sbp2,ohci1394
libata 159344 3 ata_generic,pata_amd,pata_acpi
ehci_hcd 37900 0
ohci_hcd 25348 0
scsi_mod 151436 2 sbp2,libata
forcedeth 51980 0
usbcore 146028 3 ehci_hcd,ohci_hcd
ide_generic 2176 0 [permanent]
ide_core 113996 3 ide_cd,ide_disk,ide_generic
thermal 16796 0
processor 36872 1 thermal
fan 5636 0
fbcon 42912 0
tileblit 3456 1 fbcon
font 9472 1 fbcon
bitblit 6784 1 fbcon
softcursor 3072 1 bitblit
fuse 50580 1

Any ideas ?

Boris

---

### Post by csete on 2008-04-28
Boris,

Have you figured this out at all?  I think this may be the same thing that I'm seeing and was asking about in this thread:

[http://ubuntuforums.org/showthread.php?t=771495](http://ubuntuforums.org/showthread.php?t=771495)

Any help would be greatly appreciated.

Craig

---

### Post by tlknv on 2008-04-28
I don't think that's the same problem because the error message is diffent. [http://ubuntuforums.org/showthread.php?t=771495](http://ubuntuforums.org/showthread.php?t=771495) got a message about ioctl while I get a message about permission.

---

