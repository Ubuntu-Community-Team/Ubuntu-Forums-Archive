---
title: "CD/DVD media not sensed by Nautilus (Gutsy)"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by gazilla on 2007-10-24
When new media (blank or non-blank) is inserted in the CDROM drive Nautilus ignores it completely. If I manually mount the disk all is fine, including the drive icon on the desktop.

If I start Grip and insert an audio CD then is is sensed and the track list fetched from FreeDDB.

I have checked in gconf-editor and both automount_drives and automount_media are both checked in desktop>gnome>volume_manager.

The machine is a HP6519TX, Core2 Duo, 2GB RAM running Gutsy with kernel 2.6.22-14-generic
Gutsy was installed on the new PC from Tribe 5, and has all upgrades since then.

Here are the relevant sections from dmesg...

[   15.780000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   15.780000] Uniform CD-ROM driver Revision: 3.20
[   15.780000] sr 3:0:0:0: Attached scsi CD-ROM sr0

(dmesg is silent when the disk is inserted)

...and the /dev entry...

brw-rw---- 1 root cdrom 11, 0 2007-10-24 07:39 scd0
(I am in the cdrom group)

...and lshw...

        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD-RAM writer
                product: CD/DVDW TS-L632M
                vendor: TSSTcorp
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 0A17
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open

...and the entire output from lsmod...

Module                  Size  Used by
hidp                   21248  1 
hid                    28928  1 hidp
aes                    28608  1 
af_packet              24840  4 
binfmt_misc            12936  1 
rfcomm                 42136  3 
l2cap                  26240  16 hidp,rfcomm
ppdev                  10244  0 
ipv6                  273892  38 
acpi_cpufreq           10568  1 
cpufreq_ondemand        9612  1 
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
video                  18060  8 
dock                   10656  0 
sbs                    19592  0 
container               5504  0 
button                  8976  0 
ac                      6148  0 
battery                11012  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
arc4                    2944  2 
snd_seq_oss            33152  0 
ecb                     4608  2 
blkcipher               7556  1 ecb
uvcvideo               48644  0 
snd_seq_midi            9600  0 
nvidia               6221648  26 
compat_ioctl32          2304  1 uvcvideo
iwl4965               101480  0 
videodev               29312  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
snd_rawmidi            25728  1 snd_seq_midi
iwlwifi_mac80211      175112  1 iwl4965
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
v4l2_common            18432  2 uvcvideo,videodev
cfg80211                7304  1 iwlwifi_mac80211
i2c_core               26112  1 nvidia
hci_usb                18332  3 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
bluetooth              57060  8 hidp,rfcomm,l2cap,hci_usb
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               8068  0 
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
psmouse                39952  0 
ata_generic             8452  0 
sdhci                  18828  0 
mmc_core               28420  1 sdhci
intel_agp              25620  0 
agpgart                35016  2 nvidia,intel_agp
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  6 
ext3                  133896  2 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  4 
ahci                   23300  3 
r8169                  32260  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ata_piix               17540  0 
libata                125168  3 ata_generic,ahci,ata_piix
scsi_mod              147084  5 sbp2,sr_mod,sg,sd_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  5 uvcvideo,hci_usb,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor


If this is not enough system info then please tell me the command and I will post the output.

TIA,  Gaz

---

