---
title: "Hauppauge Nova-T Old LSI L64781 Problem"
date: 2006-06-15
forum: Hardware &amp; Laptops
---

### Post by stupiduglyfool on 2006-06-15
Hi,

Hopefully this message is in the right place..

Got a slight problem getting my nova-t card fully operational under ubuntu dapper drake.. (Please note slight twist at bottom of the post)

The card I have is an old nova-t,  

dmesg output:
```

[4294693.681000] saa7146: register extension 'budget dvb'.
[4294693.683000] **** SET: Misaligned resource pointer: cbdddd02 Type 07 Len 0
[4294693.683000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[4294693.683000] ACPI: PCI Interrupt 0000:02:07.0[A] -> Link [LNKE] -> GSI 11 (l
evel, low) -> IRQ 11
[4294693.683000] saa7146: found saa7146 @ mem d09b6000 (revision 1, irq 11) (0x1
3c2,0x1005).
[4294693.683000] DVB: registering new adapter (TT-Budget/WinTV-NOVA-T  PCI).
[4294693.735000] adapter has MAC addr = 00:d0:5c:20:2d:9a
[4294693.742000] DVB: registering frontend 0 (LSI L64781 DVB-T)...

```

My nearest transmitter is uk-Bilsdale, which i get decent reception from under windows.

dvbtune -f 578000000

dvb tune gives this output:
```

dave@ubuntu-linux:~$ dvbtune -f 57800000
Using DVB card "LSI L64781 DVB-T"
tuning DVB-T (in United Kingdom) to 57800000 Hz
polling....
Getting frontend event
FE_STATUS:
polling....
polling....
polling....
polling....
Getting frontend event
FE_STATUS: FE_HAS_CARRIER
polling....
Getting frontend event
FE_STATUS:
polling....
polling....
polling....
polling....
polling....

```

lsmod output:
```

dave@ubuntu-linux:~$ lsmod
Module                  Size  Used by
nvidia               4547028  12
ipv6                  265600  6
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
speedstep_lib           4484  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
ac                      5252  1 acpi_sbs
ext2                   68360  1
nls_utf8                2176  1
ntfs                  103536  1
dm_mod                 58936  1
af_packet              22920  6
md_mod                 72532  0
lp                     11844  0
tsdev                   8000  0
snd_intel8x0           33692  1
snd_ac97_codec         92704  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
psmouse                36228  0
floppy                 62148  0
bcm43xx               124044  0
serio_raw               7300  0
budget                 11520  0
s5h1420                 9092  1 budget
l64781                  7044  1 budget
ves1820                 7044  1 budget
budget_core             9860  1 budget
saa7146                18312  2 budget,budget_core
ttpci_eeprom            2816  1 budget_core
ieee80211softmac       29696  1 bcm43xx
soundcore              10208  1 snd
pcspkr                  2180  0
stv0299                10760  1 budget
tda8083                 6276  1 budget
ves1x93                 6916  1 budget
dvb_core               82984  3 budget,budget_core,stv0299
analog                 12320  0
gameport               15496  1 analog
i2c_core               21904  11 nvidia,i2c_acpi_ec,budget,s5h1420,l64781,ves1820,budget_core,ttpci_eeprom,stv0299,tda8083,ves1x93
ieee80211              37064  2 bcm43xx,ieee80211softmac
ieee80211_crypt         6272  1 ieee80211
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
rtc                    13492  0
intel_agp              22940  1
agpgart                34888  2 nvidia,intel_agp
hw_random               5652  0
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
evdev                   9856  1
ext3                  135688  3
jbd                    58772  1 ext3
ide_generic             1536  0
uhci_hcd               33680  0
usbcore               129668  2 uhci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  8
piix                   11012  1
generic                 5124  0
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

```

There is a slight twist to these problems however, the hard disk is partitioned so i can still boot into windows, if I boot into windows first, open WinTV, then reboot into Ubuntu, everything works fine, until I turn off power.

This makes me think that there is a firmware issue here, however i've searched high and low for any information on firmware needed for this front end.

Has anyone here had experiences with this, or can suggest anything else to try, I'd really like this to be one less thing to depend on windows for?

Regards,

Dave.

---

