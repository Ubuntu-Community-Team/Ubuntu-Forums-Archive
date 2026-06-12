---
title: "Asus A8V deluxe, no sound"
date: 2005-05-03
forum: Hardware &amp; Laptops
---

### Post by DutchLau on 2005-05-03
Hello Ubuntu community,

The last few weeks I've been trying to help out all of you here in the forums, but now I need some help and it would be greatly greatly appreciated.

I have just performed a clean i386 (I don't want to go 64 yet) Ubuntu install on my PC (The specs are in my signature) Everything is working AMAZING, fast load up, quick unpackaging and an amazingly fast install, now the question is: How do I get sound working? 

At the login screen I have no sound, and in Ubuntu I have no sound, even though I've installed all the codecs. 

Could someone please please please help me out with this? It's very frustrating to have a new PC and not to be able to play sound on it. Could someone please reply?

Friendly greets,

DutchLau

---

### Post by DutchLau on 2005-05-03
Okay, I think I've figured out the problem. The realtek ALC850 driver & the AC97 codecs aren't installed so they're probably the things that are giving me hell. 

Anyone know where I can find the drivers besides on google? I've tried to find them, but I can't..

Please help,

DutchLau

---

### Post by DutchLau on 2005-05-03
If it interests anyone, the output of my lsmod is as follows:

Module                  Size  Used by
speedstep_lib           4228  0
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
vga16fb                12488  1
vgastate                8576  1 vga16fb
ipv6                  229504  9
snd_via82xx            25248  3
snd_ac97_codec         64608  1 snd_via82xx
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  2 snd_via82xx,snd_pcm
gameport                4608  1 snd_via82xx
snd_mpu401_uart         7168  1 snd_via82xx
snd_rawmidi            22944  1 snd_mpu401_uart
snd_seq_device          8332  1 snd_rawmidi
snd                    50276  11 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  3 snd
i2c_viapro              7436  0
i2c_core               21264  1 i2c_viapro
tsdev                   7488  0
ehci_hcd               29444  0
usbhid                 29376  0
af_packet              20744  2
uhci_hcd               30224  0
usbcore               107384  4 ehci_hcd,usbhid,uhci_hcd
via82cxxx              12956  1
sk98lin               149216  0
ohci1394               31876  0
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
amd64_agp              10952  1
agpgart                31784  1 amd64_agp
floppy                 54864  0
pcspkr                  3816  0
rtc                    12216  0
evdev                   9088  0
md                     43856  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
sbp2                   22408  0
ieee1394              100408  2 ohci1394,sbp2
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  0
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_generic             1664  0
ide_disk               18176  0
ide_cd                 38532  0
ide_core              118988  4 via82cxxx,ide_generic,ide_disk,ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
sr_mod                 16036  0
cdrom                  36508  2 ide_cd,sr_mod
sd_mod                 16784  3
sata_via                8196  4
sata_promise           10244  0
libata                 44548  2 sata_via,sata_promise
scsi_mod              119936  5 sbp2,sr_mod,sd_mod,sata_promise,libata
unix                   26164  736
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  71
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  2 vga16fb,vesafb
cfbimgblt               3072  2 vga16fb,vesafb
cfbfillrect             3584  2 vga16fb,vesafb

---

### Post by DutchLau on 2005-05-04
Anyone?

---

### Post by DutchLau on 2005-05-04
Okay!

I got my sound working! I had to configure Alsa and now it works perfectly! On the reboot I heard the beautiful sounds of the Ubuntu startup, I've never been so happy in my entire life

Thanks Ubuntu community,

DutchLau

---

### Post by nuclearfly on 2005-05-04
How do you reconfigure alsa?

---

