---
title: "Dummy output - Audio problem"
date: 2016-08-20
forum: Hardware
---

### Post by zlamir on 2016-08-20
Hi, i'm new to Ubuntu, also not a native English speaker so i'll do my best explaining what's going on.

I bought a new laptop a few days ago and it was working fine. But when i decided to connect some audio involved dedvices (HDMI and headphones) i started having troubles with the sound configuration. After connecting/disconnecting them i had to change manually the the audio divice who was actually on use, or else there were no audio output.
But today, the sound configuration showed this "Dummy output" on the device list and there was no sound output at all.
I've searched for solutions and i've tried some, but they hadn't worked for me. The las one i saw asked to try this on terminal:
```
 [COLOR=#333333]cd ~/[/COLOR]  wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```[COLOR=#222222][FONT=Verdana]

[/FONT][/COLOR]This was the output:

```
[COLOR=#222222][FONT=Verdana]!!################################[/FONT][/COLOR]!!ALSA Information Script v 0.4.64
!!################################


!!Script ran on: Sat Aug 20 21:26:52 UTC 2016




!!Linux Distribution
!!------------------


Ubuntu 14.04.5 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 14.04.5 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 14.04.5 LTS" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"




!!DMI Information
!!---------------


Manufacturer:      Dell Inc.
Product Name:      Inspiron 3459
Product Version:   
Firmware Version:  01.00.04




!!Kernel Information
!!------------------


Kernel release:    3.19.0-66-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes




!!ALSA Version
!!------------


Driver version:     k3.19.0-66-generic
Library version:    1.0.27.2
Utilities version:  1.0.27.2




!!Loaded ALSA modules
!!-------------------






!!Sound Servers on this system
!!----------------------------


Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes




!!Soundcards recognised by ALSA
!!-----------------------------


--- no soundcards ---




!!PCI Soundcards installed in the system
!!--------------------------------------


00:1f.3 Audio device: Intel Corporation Device 9d70 (rev 21)




!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------


00:1f.3 0403: 8086:9d70 (rev 21)
    Subsystem: 1028:06b1




!!Modprobe options (Sound related)
!!--------------------------------


snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=-2
snd_hda_intel: jackpoll_ms=500




!!Loaded sound module options
!!---------------------------




!!ALSA Device nodes
!!-----------------


crw-rw----  1 root audio 116,  1 Aug 20 18:13 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Aug 20 18:13 /dev/snd/timer




!!Aplay/Arecord output
!!--------------------


APLAY


aplay: device_list:268: no soundcards found...


ARECORD


arecord: device_list:268: no soundcards found...


!!Amixer output
!!-------------




!!Alsactl output
!!--------------


--startcollapse--
--endcollapse--




!!All Loaded Modules
!!------------------


Module
nvram
msr
uvcvideo
rtsx_usb_ms
videobuf2_vmalloc
videobuf2_memops
videobuf2_core
memstick
v4l2_common
arc4
videodev
iwlmvm
x86_pkg_temp_thermal
media
snd_hwdep
coretemp
kvm_intel
kvm
snd_pcm
mac80211
snd_seq_midi
crct10dif_pclmul
crc32_pclmul
aesni_intel
aes_x86_64
lrw
dell_wmi
snd_seq_midi_event
gf128mul
sparse_keymap
snd_rawmidi
dell_laptop
glue_helper
snd_seq
i915_bpo
iwlwifi
dcdbas
intel_ips
rfcomm
cfg80211
btusb
drm_kms_helper
drm
i8k
i2c_algo_bit
dm_multipath
scsi_dh
i2c_hid
snd_seq_device
joydev
ablk_helper
snd_timer
bnep
serio_raw
cryptd
acpi_pad
bluetooth
hid
snd
soundcore
mac_hid
shpchp
binfmt_misc
parport_pc
ppdev
lp
parport
nls_iso8859_1
btrfs
xor
raid6_pq
dm_mirror
dm_region_hash
dm_log
rtsx_usb_sdmmc
rtsx_usb
psmouse
r8169
ahci
mii
libahci
wmi
video




!!ALSA/HDA dmesg
[COLOR=#222222][FONT=Verdana]!!--------------[/FONT][/COLOR]
```

I hope you guys can help me.
Lucas.

---

