---
title: "no sound (help...)"
date: 2005-06-07
forum: Hardware &amp; Laptops
---

### Post by bach on 2005-06-07
I have just installed Ubuntu 5.04, and I have no sound. My soundcard is SounBlaster Live 5.1: 

root@edgeworth:/etc/ssh # cat /proc/asound/cards
0 [ICH5 ]: ICH4 - Intel ICH5
Intel ICH5 with AD1985 at 0xfebff800, irq 17
1 [Live ]: EMU10K1 - Sound Blaster Live!
Sound Blaster Live! (rev.10) at 0xb400, irq 19
root@edgeworth:/etc/ssh #

I followed the instructions in 

[http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)

but I still have no sound. 

Tips are extremely welcome!

---

### Post by bach on 2005-06-07
Here is the output from lsmod: 

Module                  Size  Used by
isofs                  33720  0 
udf                    77060  0 
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
ipv6                  229504  11 
emu10k1_gp              3840  0 
gameport                4608  1 emu10k1_gp
snd_emu10k1            81668  0 
snd_rawmidi            22944  1 snd_emu10k1
snd_seq_device          8332  2 snd_emu10k1,snd_rawmidi
snd_util_mem            4608  1 snd_emu10k1
snd_hwdep               9220  1 snd_emu10k1
3c59x                  37160  0 
snd_intel8x0           29984  3 
snd_ac97_codec         64608  2 snd_emu10k1,snd_intel8x0
snd_pcm_oss            47652  0 
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  5 snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  2 snd_pcm
snd                    50276  12 snd_emu10k1,snd_rawmidi,snd_seq_device,snd_hwdep,snd_int
el8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  2 snd
snd_page_alloc          9604  3 snd_emu10k1,snd_intel8x0,snd_pcm
i2c_i801                8076  0 
i2c_core               21264  1 i2c_i801
piix                    9988  1 
hw_random               5524  0 
ehci_hcd               29444  0 
uhci_hcd               30224  0 
shpchp                 86116  0 
pci_hotplug            30512  1 shpchp
intel_mch_agp          10000  0 
intel_agp              20636  1 
agpgart                31784  2 intel_mch_agp,intel_agp
floppy                 54864  0 
pcspkr                  3816  0 
rtc                    12216  0 
md                     43856  0 
dm_mod                 53116  1 
capability              5000  0 
commoncap               7808  1 capability
tsdev                   7488  0 
evdev                   9088  0 
psmouse                19336  0 
mousedev               11160  1 
parport_pc             34372  1 
lp                     10792  0 
parport                33480  2 parport_pc,lp
ide_generic             1664  0 
ide_disk               18176  0 
ide_cd                 38532  1 
cdrom                  36508  1 ide_cd
ext3                  120968  1 
jbd                    54168  1 ext3
sd_mod                 16784  3 
usb_storage            64064  0 
usbcore               107384  4 ehci_hcd,uhci_hcd,usb_storage
ide_core              118988  5 piix,ide_generic,ide_disk,ide_cd,usb_storage
ata_piix                8836  4 
libata                 44548  1 ata_piix
scsi_mod              119936  3 sd_mod,usb_storage,libata
unix                   26164  906 
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

---

