---
title: "Problems with Audigy2 Value in Ubuntu..."
date: 2005-09-01
forum: Hardware &amp; Laptops
---

### Post by Hamman on 2005-09-01
Today I got my brand new Audigy2 Value in the mail. Great! Opened the cased, put in the card and then I  booted in to windows to install drivers and to a quick testrun in GTA:SA (worked nicely).
I then booted in to Ubuntu and noticed that the volume control was gone. Apparently the card didn't work. I checked out the card on [www.alsa-project.org](www.alsa-project.org), found out that the module was called "emu10k1", so I tried doing "sudo modprobe emu10k1" but lspci still outputs the same thing:

0000:02:08.0 Multimedia audio controller: Creative Labs: Unknown device 0008

This is the output of lsmod:

snd_emu10k1            98116  0
snd_rawmidi            24928  1 snd_emu10k1
snd_seq_device          8524  2 snd_emu10k1,snd_rawmidi
snd_ac97_codec         74208  1 snd_emu10k1
snd_pcm_oss            52516  0
snd_mixer_oss          19776  1 snd_pcm_oss
snd_pcm                94920  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              25156  1 snd_pcm
snd_page_alloc          9796  2 snd_emu10k1,snd_pcm
snd_util_mem            4480  1 snd_emu10k1
snd_hwdep               9476  1 snd_emu10k1
snd                    55268  9 snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep
emu10k1                82564  0
sound                  80492  1 emu10k1
soundcore              10080  3 snd,emu10k1,sound
ac97_codec             18316  1 emu10k1
isofs                  36984  0
udf                    90308  0
fglrx                 259752  7
ipv6                  258880  9
af_packet              22280  2
shpchp                 99300  0
pci_hotplug            33584  1 shpchp
tsdev                   7616  0
sata_nv                 8580  0
libata                 49540  1 sata_nv
usbhid                 32192  0
scsi_mod              127872  1 libata
forcedeth              17408  0
ehci_hcd               32772  0
ohci_hcd               21576  0
usbcore               119224  4 usbhid,ehci_hcd,ohci_hcd
amd64_agp              11336  1
agpgart                33704  2 amd64_agp
floppy                 59152  0
pcspkr                  3560  0
rtc                    12536  0
evdev                   9408  0
md                     47504  0
dm_mod                 59708  1
capability              4744  0
commoncap               7808  1 capability
psmouse                21384  0
mousedev               11352  1
parport_pc             37444  1
lp                     11240  0
parport                36872  2 parport_pc,lp
ide_cd                 41924  1
cdrom                  40476  1 ide_cd
reiserfs              264464  1
ext2                   67144  1
ext3                  138184  1
jbd                    60888  1 ext3
mbcache                 8452  2 ext2,ext3
ide_generic             1408  0
ide_disk               20480  5
amd74xx                14044  1
ide_core              129548  4 ide_cd,ide_generic,ide_disk,amd74xx
unix                   28532  676
thermal                13384  0
processor              22516  1 thermal
fan                     4484  0
fbcon                  38016  0
font                    8256  1 fbcon
bitblit                 5568  1 fbcon
vesafb                  6820  0
cfbcopyarea             3904  1 vesafb
cfbimgblt               3008  1 vesafb
cfbfillrect             3584  1 vesafb

I've also tried modprobing snd_emu10k1, but no go. Tried with the livecd: didn't work. alsamixer and the gnome volume mixer refuses to start since they can't find any audio device.
Does anyone have the solution to this? I'd be most grateful.

---

### Post by Hamman on 2005-09-02
With kernel 2.6.11 (from the repos) the card is detected. I haven't fuddled around enough to get sound out of it yet because gnome crashes upon loading gnome-panel. I've tried disabling my overclocking but I still got the same error (even in "safe mode"). 
Does anyone know why it behaves like this?

---

