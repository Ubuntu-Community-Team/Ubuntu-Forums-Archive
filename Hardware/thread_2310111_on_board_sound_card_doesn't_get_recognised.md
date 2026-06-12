---
title: "on board sound card doesn't get recognised"
date: 2016-01-16
forum: Hardware
---

### Post by sgiannop on 2016-01-16
Hello everyone. I am having difficulties on getting my on board sound card to work with alsa. I recently replaced my old (broken) vga card (geforce 6600 LE) with a 
new one (Afox geforce G210). After that it seems that my on board AC97 sound chip is not recognisable by Linux. 

```

~$ cat /proc/asound/cards
--- no soundcards ---

```

```

~$ aplay -l
aplay: device_list:268: no soundcards found...

```

```

~$ dmesg | grep -i hda
[   21.050075] hda_intel: Disabling MSI
[   21.050098] hda-intel 0000:02:00.1: Handle VGA-switcheroo audio client
[   21.050167] hda-intel 0000:02:00.1: Disabling 64bit DMA
[   21.099660] hda-intel 0000:02:00.1: Enable delay in RIRB handling
[   22.120025] hda-intel 0000:02:00.1: Codec #1 probe error; disabling it...
[   23.132040] hda-intel 0000:02:00.1: Codec #2 probe error; disabling it...
[   24.140043] hda-intel 0000:02:00.1: Codec #3 probe error; disabling it...
[   24.177650] hda-intel 0000:02:00.1: no codecs initialized

```

any ideas?

---

### Post by sgiannop on 2016-01-16
alsa-info script gives the following output:

```

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.64
!!################################

!!Script ran on: Sat Jan 16 12:06:12 UTC 2016


!!Linux Distribution
!!------------------

Ubuntu 14.04.3 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 14.04.3 LTS" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"


!!DMI Information
!!---------------

Manufacturer:              
Product Name:      775Dual-880Pro
Product Version:   1.00
Firmware Version:  P1.70


!!Kernel Information
!!------------------

Kernel release:    3.13.0-74-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k3.13.0-74-generic
Library version:    1.0.27.2
Utilities version:  1.0.27.2


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

--- no soundcards ---


!!PCI Soundcards installed in the system
!!--------------------------------------

02:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

02:00.1 0403: 10de:0be3 (rev a1)
    Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-


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


!!Loaded sound module options
!!---------------------------


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  1 Jan 16 13:51 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Jan 16 13:51 /dev/snd/timer


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
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
snd_page_alloc
snd_seq_midi
snd_seq_midi_event
snd_rawmidi
snd_seq
snd_seq_device
snd_timer
snd
soundcore
rpcsec_gss_krb5
rfcomm
bnep
bluetooth
nfsv4
nfsd
auth_rpcgss
nfs_acl
nfs
lockd
sunrpc
fscache
arc4
rt2800usb
rt2x00usb
rt2800lib
rt2x00lib
mac80211
joydev
cfg80211
crc_ccitt
serio_raw
i2c_viapro
nvidia
drm
mac_hid
shpchp
parport_pc
ppdev
lp
parport
hid_generic
usbhid
hid
pata_acpi
usb_storage
via_rhine
mii
sata_via
pata_via


!!ALSA/HDA dmesg
!!--------------

[   19.061636] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  304.131  Sun Nov  8 21:43:33 PST 2015
[   19.103640] hda_intel: Disabling MSI
[   19.103662] hda-intel 0000:02:00.1: Handle VGA-switcheroo audio client
[   19.103731] hda-intel 0000:02:00.1: Disabling 64bit DMA
[   19.123854] hda-intel 0000:02:00.1: Enable delay in RIRB handling
[   19.477123] type=1400 audit(1452944685.113:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=341 comm="apparmor_parser"
--
[   20.057025] init: Failed to obtain startpar-bridge instance: Unknown parameter: INSTANCE
[   20.124036] hda-intel 0000:02:00.1: Codec #0 probe error; disabling it...
[   20.148027] usb 1-4: reset high-speed USB device number 4 using ehci-pci
--
[   20.576304] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   21.134068] hda-intel 0000:02:00.1: Codec #1 probe error; disabling it...
[   21.140548] FS-Cache: Loaded
--
[   22.020818] init: idmapd-mounting (/public) main process (520) killed by TERM signal
[   22.144538] hda-intel 0000:02:00.1: Codec #2 probe error; disabling it...
[   22.158311] Bluetooth: Core ver 2.17
--
[   22.240123] Bluetooth: RFCOMM ver 1.11
[   23.160055] hda-intel 0000:02:00.1: Codec #3 probe error; disabling it...
[   23.226161] init: cups main process (757) killed by HUP signal
--
[   30.975805] RPC: AUTH_GSS upcall failed. Please check user daemon is running.
[   43.316045] hda-intel 0000:02:00.1: no codecs initialized
[   43.508776] init: plymouth-splash main process (1421) terminated with status 1
--
[   52.943071] type=1400 audit(1452944717.990:70): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1606 comm="apparmor_parser"
[  293.063455] hda_intel: Disabling MSI
[  293.063476] hda-intel 0000:02:00.1: Handle VGA-switcheroo audio client
[  293.063537] hda-intel 0000:02:00.1: Disabling 64bit DMA
[  293.067937] hda-intel 0000:02:00.1: Enable delay in RIRB handling
[  293.072092] hda-intel 0000:02:00.1: spurious response 0x0:0x0, last cmd=0x0f0000
[  294.080026] hda-intel 0000:02:00.1: Codec #1 probe error; disabling it...
[  294.084378] hda-intel 0000:02:00.1: spurious response 0x0:0x0, last cmd=0x0f0000
[  295.092026] hda-intel 0000:02:00.1: Codec #2 probe error; disabling it...
[  296.104021] hda-intel 0000:02:00.1: Codec #3 probe error; disabling it...
[  301.148058] hda-intel 0000:02:00.1: no codecs initialized
[  419.687186] hda_intel: Disabling MSI
[  419.687208] hda-intel 0000:02:00.1: Handle VGA-switcheroo audio client
[  419.687271] hda-intel 0000:02:00.1: Disabling 64bit DMA
[  419.692365] hda-intel 0000:02:00.1: Enable delay in RIRB handling
[  420.700025] hda-intel 0000:02:00.1: Codec #0 probe error; disabling it...
[  421.712024] hda-intel 0000:02:00.1: Codec #1 probe error; disabling it...
[  421.716376] hda-intel 0000:02:00.1: spurious response 0x0:0x0, last cmd=0x0f0000
[  422.724025] hda-intel 0000:02:00.1: Codec #2 probe error; disabling it...
[  423.736033] hda-intel 0000:02:00.1: Codec #3 probe error; disabling it...
[  436.844094] hda-intel 0000:02:00.1: spurious response 0x0:0x0, last cmd=0x0f0004
[  443.900030] hda-intel 0000:02:00.1: no codecs initialized



```

---

