---
title: "ATI IXP 150 Sound Low Volume"
date: 2008-04-08
forum: Hardware &amp; Laptops
---

### Post by wcGary83 on 2008-04-08
Hi Everyone!


I have been working on the sound for my Toshiba Satellite P35-S605 for weeks.  I have tried everything I could find, such as messing with the Alsa Mixer, turnng off external amp, recompiling the newest Alsa drivers, adding lines to the config files, and just can't seem to find the problem!  It seems many people have run into this, with no solution!
I'm running gutsy.  There is sound, but at an extremely low volume in both the speakers and headphones...  This computer has preddy good h/K speakers, so please help!!!

Thanks!



grep -i audio
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller (rev 01)




Module                  Size  Used by
ipv6                  273892  10 
xt_limit                3584  8 
xt_tcpudp               4224  14 
ipt_LOG                 7552  8 
ipt_MASQUERADE          4608  0 
ipt_TOS                 3200  0 
ipt_REJECT              5760  1 
nf_conntrack_irc        8088  0 
nf_conntrack_ftp       11136  0 
xt_state                3456  6 
wlan_wep                8064  1 
wlan_tkip              13696  0 
af_packet              24840  4 
binfmt_misc            12936  1 
radeon                125472  2 
drm                    83348  3 radeon
ppdev                  10244  0 
acpi_cpufreq           10568  0 
cpufreq_ondemand        9612  2 
cpufreq_userspace       5280  0 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
video                  18060  0 
button                  8976  0 
battery                11012  0 
container               5504  0 
dock                   10656  0 
ac                      6148  0 
sbs                    19592  0 
ide_scsi               19080  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_atiixp             21644  2 
snd_ac97_codec        101924  1 snd_atiixp
ac97_bus                3456  1 snd_ac97_codec
snd_pcm_oss            43008  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                80644  3 snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4996  0 
snd_seq_oss            35584  0 
snd_seq_midi            9728  0 
snd_rawmidi            26112  1 snd_seq_midi
joydev                 11328  0 
snd_seq_midi_event      8704  2 snd_seq_oss,snd_seq_midi
pcmcia                 41388  0 
wlan_scan_sta          15104  1 
sdhci                  18828  0 
snd_seq                54384  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ath_rate_sample        14208  1 
mmc_core               28420  1 sdhci
snd_timer              24580  2 snd_pcm,snd_seq
snd_seq_device          9740  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath_pci                98336  0 
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_piix4               9740  0 
wlan                  206660  6 wlan_wep,wlan_tkip,wlan_scan_sta,ath_rate_sample,ath_pci
pcspkr                  4224  0 
serio_raw               8068  0 
psmouse                39952  0 
ati_agp                10124  1 
agpgart                35016  2 drm,ati_agp
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
i2c_core               26112  1 i2c_piix4
snd                    56708  15 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11656  2 snd_atiixp,snd_pcm
ath_hal               192720  3 ath_rate_sample,ath_pci
evdev                  11136  5 
iptable_nat             8708  0 
nf_nat                 20140  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19724  8 iptable_nat
nf_conntrack           65288  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nfnetlink               6936  3 nf_nat,nf_conntrack_ipv4,nf_conntrack
iptable_mangle          3840  0 
iptable_filter          3968  1 
ip_tables              13924  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16260  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,iptable_nat,ip_tables
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
usbhid                 29536  0 
hid                    28928  1 usbhid
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
ide_disk               18560  3 
8139cp                 25088  0 
ata_generic             8452  0 
libata                125168  1 ata_generic
scsi_mod              147084  3 ide_scsi,sbp2,libata
ehci_hcd               36492  0 
ohci_hcd               22916  0 
8139too                27776  0 
mii                     6528  2 8139cp,8139too
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
atiixp                  7056  0 [permanent]
ide_core              116804  4 ide_scsi,ide_cd,ide_disk,atiixp
usbcore               138632  4 usbhid,ehci_hcd,ohci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

---

