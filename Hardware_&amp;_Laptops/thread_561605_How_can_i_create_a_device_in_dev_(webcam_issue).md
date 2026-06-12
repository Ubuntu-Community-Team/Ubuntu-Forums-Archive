---
title: "How can i create a device in /dev? (webcam issue)"
date: 2007-09-27
forum: Hardware &amp; Laptops
---

### Post by canceLinux on 2007-09-27
i've installed my webcam driver & loaded the module.. but there isn't a /dev/video* :? how can i add it manually??

i've add video0 by this command:

*mknod /dev/video0 c 81 0*

but this device doesn't work like my webcam. no stream..

here is dmesg: 

[I]Linux video capture interface: v2.00
stk11xx: Syntek USB2.0 webcam driver startup
usbcore: registered new interface driver usb_stk11xx_driver
stk11xx: v1.0.0 : Syntek USB Video Camera
[/I]
thanks :(

---

### Post by geraldm on 2007-09-27
loaded module ?? shoude be modules ?? - ehci_hcd videodev v4l2_common

There should have been more information from your logs.  Here is some output from a 
different version of stk11xx:

stk11xx: Syntek USB2.0 - STK-1125 based webcam found.
usb 4-2: USB disconnect, address 2
stk11xx: Release: 0005
stk11xx: Number of interfaces : 1
stk11xx: Initialize USB2.0 Syntek Camera
stk11xx: Syntek USB2.0 Camera is ready
stk11xx: Syntek USB2.0 Camera is now controlling video device /dev/video0
usbcore: registered new interface driver usb_stk11xx_driver
stk11xx: v0.0.1 : Syntek USB Video Camera

That shows device at /dev/video0
Possibly there should have been error messages in /var/log/syslog if all modules were 
loaded.  If the driver could not create /dev/videoX then it should provide an error message
OR that is a bug in the driver.

mknod command looked good.  Check the permissions with command 

ls -l /dev/video0
crw-rw---- 1 root video 81, 0 2006-02-06 21:52 /dev/video0

Gerald

---

### Post by canceLinux on 2007-09-29
my lsmod output:
[I]
Module                  Size  Used by
cpufreq_ondemand        7052  0 
pcspkr                  2944  0 
firewire_ohci          15360  0 
firewire_core          36032  1 firewire_ohci
crc_itu_t               2304  1 firewire_core
ohci1394               31408  0 
ieee1394               81720  1 ohci1394
sdhci                  14860  0 
mmc_core               23300  1 sdhci
rtc_cmos                7328  0 
rtc_core               14984  1 rtc_cmos
rtc_lib                 2944  1 rtc_core
iwl4965               188904  0 
mac80211              124292  1 iwl4965
cfg80211                5128  1 mac80211
serio_raw               5764  0 
sg                     26652  0 
intel_agp              21524  0 
thermal                10888  0 
fan                     3844  0 
joydev                  8512  0 
button                  6160  0 
battery                 8324  0 
ac                      4100  0 
snd_hda_intel         277532  1 
snd_seq_oss            29312  0 
snd_seq_midi_event      6528  1 snd_seq_oss
snd_seq                46672  4 snd_seq_oss,snd_seq_midi_event
snd_seq_device          6924  2 snd_seq_oss,snd_seq
tsdev                   6720  0 
nvidia               6213200  56 
agpgart                27224  2 intel_agp,nvidia
i2c_core               20352  1 nvidia
snd_hwdep               7300  1 snd_hda_intel
snd_pcm_oss            37024  0 
snd_pcm                69124  2 snd_hda_intel,snd_pcm_oss
snd_timer              19332  2 snd_seq,snd_pcm
snd_page_alloc          7816  2 snd_hda_intel,snd_pcm
psmouse                35984  0 
evdev                   8192  1 
snd_mixer_oss          14592  1 snd_pcm_oss
usbhid                 38048  0 
snd                    45028  11 snd_hda_intel,snd_seq_oss,snd_seq,snd_seq_device,snd_hwdep,snd_pcm_oss,snd_pcm,snd_timer,snd_mixer_oss
hid                    26240  1 usbhid
soundcore               6496  1 snd
ff_memless              5256  1 usbhid
acpi_cpufreq            7720  1 
freq_table              3984  2 cpufreq_ondemand,acpi_cpufreq
processor              24788  2 thermal,acpi_cpufreq
asus_acpi              15004  0 
stk11xx                57988  0 
videodev               26752  1 stk11xx
v4l2_common            15744  1 videodev
v4l1_compat            14084  1 videodev
atl1                   30476  0 
mii                     4864  1 atl1
reiserfs              234880  2 
sr_mod                 14756  0 
cdrom                  34336  1 sr_mod
sd_mod                 22784  4 
ehci_hcd               30732  0 
uhci_hcd               22416  0 
usbcore               112520  5 usbhid,stk11xx,ehci_hcd,uhci_hcd
ata_piix               11652  0 
ahci                   19076  3 
ata_generic             5380  0 
libata                108084  3 ata_piix,ahci,ata_generic[/I]


should be good but here is vlc output:

[00000288] v4l demuxer error: cannot open device (there is no device)

how can i control it?

---

