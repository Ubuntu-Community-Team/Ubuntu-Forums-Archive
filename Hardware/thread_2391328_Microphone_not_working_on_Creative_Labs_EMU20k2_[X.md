---
title: "Microphone not working on Creative Labs EMU20k2 [X-Fi Titanium Series]"
date: 2018-05-08
forum: Hardware
---

### Post by l-alebarde on 2018-05-08
Hi all,


I have a dual boot Windows 7 / Debian Wheezy. My sound card device is a Creative Labs EMU20k2 [X-Fi Titanium Series]. Sound works well, the microphone works under Windows, but I cannot manage to make it work under Linux. I have followed many helpfull threads, but it still does not work. Of course, I checked alsamixer, AudioMixer and the PulseAudio Volume Controller to check that the microphone is active everywhere, not muted, with appropriate volume.




Here is part of my alsa-info (the whole of it [here]("https://pastebin.com/xWH25vNV")): 

```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.64
!!################################


!!Script ran on: Thu Jun  7 13:30:54 UTC 2018




!!Linux Distribution
!!------------------


Debian GNU/Linux 8 \n \l PRETTY_NAME="Debian GNU/Linux 8 (jessie)" NAME="Debian GNU/Linux" ID=debian HOME_URL="http://www.debian.org/" SUPPORT_URL="http://www.debian.org/support" BUG_REPORT_URL="https://bugs.debian.org/"




!!DMI Information
!!---------------


Manufacturer:      Dell Inc.
Product Name:      Studio XPS 8000
Product Version:   
Firmware Version:  A01
Board Vendor:      Dell Inc.
Board Name:        0X231R




!!ACPI Device Status Information
!!---------------


/sys/bus/acpi/devices/PNP0103:00/status      15
/sys/bus/acpi/devices/PNP0C0C:00/status      11
/sys/bus/acpi/devices/PNP0C0F:00/status      9
/sys/bus/acpi/devices/PNP0C0F:01/status      9
/sys/bus/acpi/devices/PNP0C0F:02/status      9
/sys/bus/acpi/devices/PNP0C0F:03/status      9
/sys/bus/acpi/devices/PNP0C0F:04/status      9
/sys/bus/acpi/devices/PNP0C0F:05/status      9
/sys/bus/acpi/devices/PNP0C0F:06/status      9
/sys/bus/acpi/devices/PNP0C0F:07/status      9




!!Kernel Information
!!------------------


Kernel release:    3.16.0-4-amd64
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         unknown
SMP Enabled:       Yes




!!ALSA Version
!!------------


Driver version:     k3.16.0-4-amd64
Library version:    1.0.28
Utilities version:  1.0.28




!!Loaded ALSA modules
!!-------------------


snd_ctxfi




!!Sound Servers on this system
!!----------------------------


Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


Jack:
      Installed - Yes (/usr/bin/jackd)
      Running - No




!!Soundcards recognised by ALSA
!!-----------------------------


 0 [XFi            ]: SB-XFi - Creative X-Fi
                      Creative X-Fi 20K2 Unknown




!!PCI Soundcards installed in the system
!!--------------------------------------


04:00.0 Audio device: Creative Labs EMU20k2 [X-Fi Titanium Series] (rev 03)




!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------


04:00.0 0403: 1102:000b (rev 03)
    Subsystem: 1102:0044




!!Modprobe options (Sound related)
!!--------------------------------


snd_pcsp: index=-2
snd_usb_audio: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_ctxfi: index=0




!!Loaded sound module options
!!---------------------------


!!Module: snd_ctxfi
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : 0,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    multiple : 2
    reference_rate : 48000
    subsystem : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    use_system_timer : N




!!ALSA Device nodes
!!-----------------


crw-rw----+ 1 root audio 116,  2 Jun  7 09:29 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  4 Jun  7 15:19 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  3 Jun  7 15:19 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  5 Jun  7 09:29 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116,  6 Jun  7 09:29 /dev/snd/pcmC0D2p
crw-rw----+ 1 root audio 116,  7 Jun  7 09:29 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116,  8 Jun  7 09:31 /dev/snd/pcmC0D4p
crw-rw----+ 1 root audio 116,  1 Jun  7 09:29 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Jun  7 09:29 /dev/snd/timer


/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Jun  7 09:29 .
drwxr-xr-x 3 root root 240 Jun  7 09:29 ..
lrwxrwxrwx 1 root root  12 Jun  7 09:29 pci-0000:04:00.0 -> ../controlC0




!!Aplay/Arecord output
!!--------------------


APLAY


**** List of PLAYBACK Hardware Devices ****
card 0: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
  Subdevices: 256/256
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
etc

card 0: XFi [Creative X-Fi], device 1: ctxfi [Surround]
  Subdevices: 256/256
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
etc

card 0: XFi [Creative X-Fi], device 2: ctxfi [Center/LFE]
  Subdevices: 256/256
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
etc

card 0: XFi [Creative X-Fi], device 3: ctxfi [Side]
  Subdevices: 256/256
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
etc

card 0: XFi [Creative X-Fi], device 4: ctxfi [IEC958 Non-audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


ARECORD


**** List of CAPTURE Hardware Devices ****
card 0: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


!!Amixer output
!!-------------


!!-------Mixer controls for card 0 [XFi]


Card hw:0 'XFi'/'Creative X-Fi 20K2 Unknown'
  Mixer name    : '20K2'
  Components    : ''
  Controls      : 1052
  Simple ctrls  : 10
Simple mixer control 'Master',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 256 [100%] [0.00dB] Capture 256 [100%] [0.00dB]
  Front Right: Playback 256 [100%] [0.00dB] Capture 256 [100%] [0.00dB]
Simple mixer control 'PCM',0
  Capabilities: pvolume cvolume cswitch cswitch-joined
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 256 [100%] [0.00dB] Capture 256 [100%] [0.00dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] Capture 256 [100%] [0.00dB] [on]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 256 [100%] [0.00dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 256 [100%] [0.00dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] [on]
Simple mixer control 'Center/LFE',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 256 [100%] [0.00dB] [off]
  Front Right: Playback 256 [100%] [0.00dB] [off]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 256 [100%] [0.00dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume cvolume cswitch cswitch-joined
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 256 [100%] [0.00dB] Capture 0 [0%] [-99999.99dB] [off]
  Front Right: Playback 256 [100%] [0.00dB] Capture 0 [0%] [-99999.99dB] [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume cvolume cswitch cswitch-joined
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 256 [100%] [0.00dB] Capture 256 [100%] [0.00dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] Capture 256 [100%] [0.00dB] [on]
Simple mixer control 'IEC958',0
  Capabilities: pvolume cvolume cswitch cswitch-joined
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 256 [100%] [0.00dB] Capture 256 [100%] [0.00dB] [off]
  Front Right: Playback 256 [100%] [0.00dB] Capture 256 [100%] [0.00dB] [off]
Simple mixer control 'Digital',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 256
  Mono:
  Front Left: Playback 256 [100%] [0.00dB] [off]
  Front Right: Playback 256 [100%] [0.00dB] [off]




!!Alsactl output
!!--------------


--startcollapse--
state.XFi {
    control.1 {
        iface PCM
        name 'Playback Channel Map'
        value.0 0
        value.1 0
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        comment {
            access read
            type INTEGER
            count 8
            range '0 - 36'
        }
    }
    control.2 {
        iface PCM
        name 'Playback Channel Map'
        index 1
        value.0 0
        value.1 0
        value.2 0
        value.3 0
        value.4 0
        value.5 0
        value.6 0
        value.7 0
        comment {
            access read
            type INTEGER
            count 8
            range '0 - 36'
        }
    }
etc



!!All Loaded Modules
!!------------------


Module
bnep
bluetooth
6lowpan_iphc
crc16
cfg80211
rfkill
pci_stub
binfmt_misc
vboxpci
vboxnetadp
vboxnetflt
vboxdrv
nfsd
auth_rpcgss
oid_registry
nfs_acl
nfs
lockd
fscache
sunrpc
ip6t_REJECT
xt_hl
ip6t_rt
nf_conntrack_ipv6
nf_defrag_ipv6
ipt_REJECT
xt_LOG
xt_limit
xt_tcpudp
xt_addrtype
nf_conntrack_ipv4
nf_defrag_ipv4
xt_conntrack
ip6table_filter
ip6_tables
nf_conntrack_netbios_ns
nf_conntrack_broadcast
nf_nat_ftp
nf_nat
nf_conntrack_ftp
nf_conntrack
iptable_filter
ip_tables
x_tables
evdev
iTCO_wdt
iTCO_vendor_support
kvm_intel
kvm
pcspkr
serio_raw
dcdbas
lpc_ich
button
mfd_core
i7core_edac
shpchp
edac_core
processor
thermal_sys
nvidia
drm
snd_ctxfi
snd_pcm
snd_timer
snd
soundcore
it87
coretemp
adt7475
hwmon_vid
loop
fuse
parport_pc
ppdev
lp
parport
autofs4
btrfs
xor
raid6_pq
dm_mod
usb_storage
sg
sd_mod
crc_t10dif
sr_mod
crct10dif_generic
cdrom
crct10dif_common
hid_generic
usbhid
hid
ata_generic
ata_piix
broadcom
ehci_pci
crc32c_intel
ehci_hcd
firewire_ohci
libata
tg3
i2c_i801
psmouse
ptp
scsi_mod
pps_core
i2c_core
firewire_core
libphy
usbcore
crc_itu_t
usb_common




!!ALSA/HDA dmesg
!!--------------









```



Any idea please ?

---

### Post by Yellow Pasque on 2018-05-09
Have you tried a LiveUSB/CD of a recent distro, like Ubuntu 18.04?

---

