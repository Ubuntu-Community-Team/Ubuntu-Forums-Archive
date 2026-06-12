---
title: "laptop: winxp in virtualbox and bluetooth?"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by justDIY on 2007-04-27
I recently purchased a bluetooth phone, and I want to communicate with it, using bluetooth

the phone has some proprietary windows-only software, so I'd like to get bluetooth working under my virtualized install of windows xp..

my host OS is ubuntu edgy, and I'm running the latest virtualbox precompiled binary

my laptop has an internal bluetooth radio, which seems to be connected via USB when the RF kill switch is inactive.  virtualbox sees the device as an Broadcom HP Integrated Module, but it shows it as "IN USE".  I'm not sure how to remove it from use under linux, so it can be detected by the windows xp guest.

here's my lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 03f0:171d Hewlett-Packard 
Bus 001 Device 004: ID 08ff:2580 AuthenTec, Inc. 
Bus 001 Device 002: ID 0424:2503 Standard Microsystems Corp. 
Bus 001 Device 001: ID 0000:0000 

lsmod:
Module                  Size  Used by
michael_mic             3712  6 
arc4                    3200  6 
ieee80211_crypt_tkip    12416  3 
binfmt_misc            13448  1 
l2cap                  27136  2 
vboxdrv                34692  2 
ipv6                  272288  19 
i915                   21632  2 
drm                    74644  3 i915
speedstep_centrino      9760  1 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       2944  1 
cpufreq_ondemand        8876  1 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sbs                    16804  0 
sony_acpi               6412  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
i2c_core               23424  1 i2c_ec
hotkey                 11556  0 
dev_acpi               12292  0 
button                  7952  0 
battery                11652  0 
container               5632  0 
ac                      6788  0 
asus_acpi              17688  0 
sbp2                   24584  0 
lp                     12964  0 
af_packet              24584  6 
snd_hda_intel          20116  5 
snd_hda_codec         164608  1 snd_hda_intel
snd_pcm_oss            47360  0 
snd_pcm                84612  5 snd_hda_intel,snd_hda_codec,snd_pcm_oss
pcmcia                 40380  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_seq_dummy           4996  0 
snd_seq_oss            36480  0 
snd_seq_midi            9984  0 
snd_rawmidi            27264  1 snd_seq_midi
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
sg                     37404  0 
snd_seq                59120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ipw3945               124576  1 
snd_timer              25348  4 snd_pcm,snd_seq
joydev                 11200  0 
tsdev                   9152  0 
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           28812  1 
rsrc_nonstatic         15360  1 yenta_socket
ieee80211              35272  1 ipw3945
ieee80211_crypt         7552  2 ieee80211_crypt_tkip,ieee80211
hci_usb                18068  2 
sdhci                  20108  0 
mmc_core               32136  1 sdhci
bluetooth              53476  6 l2cap,hci_usb
tg3                   107652  0 
tifm_7xx1               9472  0 
tifm_core              10496  1 tifm_7xx1
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 42144  0 
pcspkr                  4352  0 
snd                    58372  16 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
pci_hotplug            32828  1 shpchp
tpm_infineon            9496  0 
tpm                    17568  1 tpm_infineon
tpm_bios                8832  1 tpm
hw_random               7320  0 
intel_agp              26012  1 
agpgart                34888  3 drm,intel_agp
psmouse                41352  0 
serio_raw               8452  0 
evdev                  11392  2 
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
ext3                  142856  1 
jbd                    62228  1 ext3
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
uhci_hcd               24968  0 
ehci_hcd               34696  0 
usbcore               134912  4 hci_usb,uhci_hcd,ehci_hcd
ide_generic             2432  0 
sd_mod                 22656  3 
ahci                   20356  2 
libata                 74892  1 ahci
scsi_mod              144648  5 sbp2,sg,sd_mod,ahci,libata
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
piix                   11780  1 
generic                 6276  0 
thermal                15624  0 
processor              31560  2 speedstep_centrino,thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

---

