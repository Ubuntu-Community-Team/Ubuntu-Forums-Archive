---
title: "webcam and wireless issues on toshiba l305d"
date: 2009-01-20
forum: Hardware
---

### Post by pacdidj on 2009-01-20
Hi,

I was wondering if anyone has any insight into 2 issues I've had with a new Toshiba laptop running intrepid.

The first, which I've actually found a clumsy workaround for is a problem with the Atheros wireless card on my machine.  I got the card working most of the time using ath5k with the instructions given here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros")
Occasionally though, the card fails to initialize on startup, and when this happens Gnome Network Manager won't recognize wireless capability on any subsequent restart until I shut down the computer, remove its battery, replace the battery and reboot.

The second issue is that the integrated webcam in this machine is not recognized by any program that attempts to access it.  The only exception to this was today, after installing the latest updates to cheese and v4l and restarting, the system was able to access the webcam perfectly.  But, after restarting the machine again it is no longer recognized.

Here's the lsusb output for my webcam:
> Bus 006 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 

gstreamer-properties identifies the camera as: 
> CNF7051
But, when I attempt to test the camera in gstreamer-properties, I get this error message:
> gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Could not get/set settings from/on resource. [v4l_calls.c(409): gst_v4l_set_chan_norm (): /GstPipeline:pipeline0/GstV4lSrc:v4lsrc2:
Error setting the channel/norm settings: Invalid argument]


I've tried downloading and building the latest uvcvideo source as well, with no effect.

 I'd appreciate any feedback from people who may have found solutions or workarounds for either of these 2 problems.

See below for the output of lsmod on my system, if that's of any help.

Thanks in advance,
Phil

output of lsmod:
> ipv6                  314312  14 
af_packet              29568  4 
binfmt_misc            18700  1 
rfcomm                 51104  0 
bridge                 64544  0 
stp                    11268  1 bridge
bnep                   23168  2 
sco                    20612  2 
l2cap                  33280  6 rfcomm,bnep
bluetooth              70820  6 rfcomm,bnep,sco,l2cap
ppdev                  16904  0 
powernow_k8            23684  1 
cpufreq_userspace      12420  0 
cpufreq_stats          14468  0 
cpufreq_powersave      10368  0 
cpufreq_ondemand       16400  1 
freq_table             13568  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    16392  0 
sbs                    22288  0 
sbshc                  14592  1 sbs
wmi                    15808  0 
container              12288  0 
pci_slot               13704  0 
iptable_filter         11520  0 
ip_tables              28176  1 iptable_filter
x_tables               31752  1 ip_tables
parport_pc             44200  0 
lp                     19588  0 
parport                50096  3 ppdev,parport_pc,lp
joydev                 20736  0 
snd_hda_intel         489264  3 
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                99208  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            42368  0 
snd_seq_midi           15872  0 
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34320  2 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    79432  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
arc4                   10368  2 
psmouse                51612  0 
i2c_piix4              17936  0 
ecb                    11520  2 
pcspkr                 11136  0 
k8temp                 13568  0 
uvcvideo               72844  0 
serio_raw              14596  0 
evdev                  20512  12 
crypto_blkcipher       27780  1 ecb
i2c_core               36128  1 i2c_piix4
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm
usb_storage            92864  0 
videodev               53632  1 uvcvideo
libusual               31784  1 usb_storage
v4l1_compat            24068  2 uvcvideo,videodev
v4l2_compat_ioctl32    19712  1 videodev
ath5k                 115584  0 
lbm_cw_mac80211       242360  1 ath5k
lbm_cw_cfg80211        45088  2 ath5k,lbm_cw_mac80211
led_class              13192  1 ath5k
fglrx                2082944  29 
video                  28948  0 
output                 11776  1 video
battery                21128  0 
button                 15904  0 
ac                     13448  0 
shpchp                 42140  0 
pci_hotplug            39472  1 shpchp
ext3                  150544  1 
jbd                    66472  1 ext3
mbcache                17924  1 ext3
sr_mod                 24644  0 
cdrom                  47784  1 sr_mod
pata_acpi              13568  0 
sd_mod                 45864  3 
crc_t10dif             10240  1 sd_mod
sg                     45408  0 
pata_atiixp            14208  0 
ata_generic            14212  0 
ehci_hcd               48908  0 
ohci_hcd               34972  0 
ahci                   43148  2 
usbcore               175376  6 uvcvideo,usb_storage,libusual,ehci_hcd,ohci_hcd
r8169                  40196  0 
libata                200160  4 pata_acpi,pata_atiixp,ata_generic,ahci
scsi_mod              183160  5 usb_storage,sr_mod,sd_mod,sg,libata
dock                   18464  1 libata
thermal                27424  0 
processor              47800  2 powernow_k8,thermal
fan                    13576  0 
fbcon                  51200  0 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit
fuse                   68288  3 


---

### Post by StuartCarter on 2009-07-04
I am having the same problem with the same device.

---

