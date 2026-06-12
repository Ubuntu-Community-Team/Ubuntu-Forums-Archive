---
title: "Not able to use my USB wireless adaptor (BUFFALO WLI-U2-KG54-AI )"
date: 2009-05-12
forum: Hardware
---

### Post by skdevnath on 2009-05-12
When I connect the device, I see that this device get recognized as input device or CD rom

ay 12 03:01:47 sandip-mce kernel: [  276.456043] usb 6-7: new high speed USB device using ehci_hcd and address 5
May 12 03:01:47 sandip-mce kernel: [  276.623053] usb 6-7: configuration #1 chosen from 1 choice
May 12 03:01:47 sandip-mce kernel: [  276.658491] **input: BUFFALO WLI-U2-KG54-AI as /devices/pci0000:00/0000:00:13.5/usb6/6-7/6-7:1.0/input/input7**
May 12 03:01:47 sandip-mce kernel: [  276.710036] **input,hidraw0: USB HID v1.00 Keyboard [BUFFALO WLI-U2-KG54-AI**] on usb-0000:00:13.5-7
May 12 03:02:07 sandip-mce kernel: [  296.783260] usb 6-7: USB disconnect, address 5
May 12 03:02:07 sandip-mce kernel: [  297.088039] usb 6-7: new high speed USB device using ehci_hcd and address 6
May 12 03:02:07 sandip-mce kernel: [  297.253402] usb 6-7: configuration #1 chosen from 1 choice
May 12 03:02:07 sandip-mce kernel: [  297.255313] scsi8 : SCSI emulation for USB Mass Storage devices
May 12 03:02:13 sandip-mce kernel: [  302.257222] scsi 8:0:0:0: CD-ROM            BUFFALO  WLI-U2-KG54-CD   1.00 PQ: 0 ANSI: 0 CCS
May 12 03:02:13 sandip-mce kernel: [  302.264568] sr1: scsi3-mmc drive: 0x/0x caddy
May 12 03:02:13 sandip-mce kernel: [  302.265085] sr 8:0:0:0: Attached scsi generic sg7 type 5
May 12 03:02:34 sandip-mce kernel: [  323.314125] sr 8:0:0:0: ioctl_internal_command return code = 8000002
May 12 03:02:34 sandip-mce kernel: [  323.314133]    : Sense Key : No Sense [current] 
May 12 03:02:34 sandip-mce kernel: [  323.314137]    : Add. Sense: No additional sense information
May 12 03:02:34 sandip-mce kernel: [  323.573390] sr 8:0:0:0: ioctl_internal_command return code = 8000002
May 12 03:02:34 sandip-mce kernel: [  323.573397]    : Sense Key : No Sense [current] 

other details:
-------------------

root@sandip-mce:~# uname -a
Linux sandip-mce 2.6.27-11-generic #1 SMP Wed Apr 1 20:53:41 UTC 2009 x86_64 GNU/Linux

root@sandip-mce:~# uname -a
Linux sandip-mce 2.6.27-11-generic #1 SMP Wed Apr 1 20:53:41 UTC 2009 x86_64 GNU/Linux
root@sandip-mce:~# lsmod 
Module                  Size  Used by
ipv6                  314312  12 
af_packet              29568  2 
binfmt_misc            18700  1 
lirc_mceusb2           21764  0 
lirc_dev               22216  1 lirc_mceusb2
rfcomm                 51104  0 
sco                    20612  2 
bridge                 64544  0 
stp                    11268  1 bridge
bnep                   23168  2 
l2cap                  33280  6 rfcomm,bnep
bluetooth              70820  6 rfcomm,sco,bnep,l2cap
ppdev                  17032  0 
powernow_k8            23812  1 
cpufreq_ondemand       16400  1 
cpufreq_powersave      10368  0 
cpufreq_stats          14468  0 
cpufreq_conservative    16392  0 
freq_table             13568  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace      12420  0 
wmi                    15808  0 
video                  29204  0 
output                 11776  1 video
sbs                    22288  0 
sbshc                  14592  1 sbs
pci_slot               13704  0 
container              12288  0 
battery                21128  0 
iptable_filter         11520  0 
ip_tables              28176  1 iptable_filter
x_tables               31752  1 ip_tables
ac                     13448  0 
sbp2                   32652  0 
lp                     19588  0 
snd_hda_intel         492208  0 
snd_cmipci             49952  3 
snd_pcm_oss            52608  0 
snd_mixer_oss          25216  1 snd_pcm_oss
gameport               21776  1 snd_cmipci
snd_opl3_lib           20736  1 snd_cmipci
snd_pcm                99336  3 snd_hda_intel,snd_cmipci,snd_pcm_oss
snd_hwdep              16904  1 snd_opl3_lib
snd_mpu401_uart        16768  1 snd_cmipci
snd_seq_dummy          11524  0 
snd_seq_oss            42496  0 
snd_seq_midi           15872  0 
snd_rawmidi            34176  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34320  3 snd_opl3_lib,snd_pcm,snd_seq
snd_seq_device         16404  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                51612  0 
snd                    79432  19 snd_hda_intel,snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_opl3_lib,snd_pcm,snd_hwdep,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              14596  0 
pcspkr                 11136  0 
k8temp                 13568  0 
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm
soundcore              16800  1 snd
i2c_piix4              17936  0 
evdev                  20512  6 
i2c_core               36000  1 i2c_piix4
parport_pc             44200  1 
parport                49968  3 ppdev,lp,parport_pc
button                 15904  0 
shpchp                 42140  0 
pci_hotplug            39216  1 shpchp
ext3                  150544  1 
jbd                    66856  1 ext3
mbcache                17924  1 ext3
usb_storage            94784  0 
sr_mod                 24644  0 
cdrom                  47656  1 sr_mod
libusual               35752  1 usb_storage
usbhid                 39648  0 
hid                    58944  1 usbhid
sd_mod                 45864  5 
crc_t10dif             10240  1 sd_mod
pata_atiixp            14208  0 
ata_generic            14212  0 
sg                     45408  0 
ohci1394               41524  0 
ieee1394              110464  2 sbp2,ohci1394
r8169                  40452  0 
mii                    14592  1 r8169
pata_acpi              13568  0 
ehci_hcd               49420  0 
ohci_hcd               34972  0 
ahci                   43148  3 
usbcore               175760  7 lirc_mceusb2,usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd
libata                201184  4 pata_atiixp,ata_generic,pata_acpi,ahci
scsi_mod              183288  6 sbp2,usb_storage,sr_mod,sd_mod,sg,libata
dock                   18464  1 libata
thermal                27552  0 
processor              47800  2 powernow_k8,thermal
fan                    13576  0 
fbcon                  51200  0 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit
fuse                   68288  5 
root@sandip-mce:~#

---

### Post by skdevnath on 2009-05-17
Any comment, how I can use my USB Wifi adaptor with my ubuntu ?


Linux sandip-mce 2.6.27-11-generic #1 SMP Wed Apr 1 20:53:41 UTC 2009 x86_64 GNU/Linux


Do you folks think that 64 bit US wouldn't be a good idea to recognize my USB wifi adpator ? do you think I should try 32bit OS instead ?

---

### Post by coffeeaddict22 on 2009-05-17
Hi,
Wireless has come a long way recently, so I wouldn't give up hope (yet).

Type in ```
nm-tool
lshw -C network
```
(two separate commands); post the results back.

---

