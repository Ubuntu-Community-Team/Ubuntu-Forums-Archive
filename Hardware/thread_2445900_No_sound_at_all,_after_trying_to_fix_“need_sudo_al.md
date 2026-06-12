---
title: "No sound at all, after trying to fix “need sudo alsa force-reload after boot&quot;"
date: 2020-06-21
forum: Hardware
---

### Post by osirus83 on 2020-06-21
[COLOR=#242729][FONT=Arial]I am using Ubuntu 20.04 (and I am new to linux at all). Every time after booting I had no sound, I needed to use "sudo alsa force-reload" to make sound working.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I tried to fix this and searched for several possible solutions on the www. After trying a lot of things, now I have no sound at all. Alsa force-reload doesn't work anymore. Some outputs I get:
[/FONT][/COLOR]
```
sudo alsa force-reload
```[INDENT][FONT=inherit]*Unloading ALSA sound driver modules: snd-hda-intel snd-intel-dspcfg snd-hda-codec snd-hda-core snd-hwdep snd-pcm snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer.* 
*Loading ALSA sound driver modules: snd-hda-intel snd-intel-dspcfg snd-hda-codec snd-hda-core snd-hwdep snd-pcm snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer.*[/FONT]
[/INDENT]
```
alsamixer
```[INDENT][FONT=inherit]*cannot open mixer no such file or directory*[/FONT]
[/INDENT]
```
sudo aplay -l
```[INDENT][FONT=inherit]*aplay: device_list:274: no soudcards found...*[/FONT]
[/INDENT]
```
alsactl restore
```[INDENT][FONT=inherit]*alsactl: load_state:1683: Cannot open /var/lib/alsa/asound.state for reading: No such file or directory*[/FONT]
[/INDENT]
```
sudo modprobe snd_hda_intel
```[INDENT][FONT=inherit]did nothing at all[/FONT]
[/INDENT]
```
lspci -v | grep -A7 -i "audio"
```[INDENT][FONT=inherit]did nothing at all

[/FONT]
[/INDENT]
[COLOR=#242729][FONT=Arial]In my sound settings there is only the dummy output. Before, when I used the als force-reload command it changed to a soundcard. Now it doesn't change anymore.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Really tried a lot of things, don't know exactly what anymore... all the solutions I could find when google my problem for two days. Is there a way to reset all the sound things to stock Ubuntu files and settings? What information do you need for that?[/FONT][/COLOR]

---

### Post by Yellow Pasque on 2020-06-22
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by osirus83 on 2020-06-22
[http://alsa-project.org/db/?f=3a53993cb5df1b9e11e2ebabc55607af8460e2ea](http://alsa-project.org/db/?f=3a53993cb5df1b9e11e2ebabc55607af8460e2ea)

> [COLOR=#000000]!!################################[/COLOR]!!ALSA Information Script v 0.4.65
!!################################

!!Script ran on: Mon Jun 22 15:35:44 UTC 2020


!!Linux Distribution
!!------------------

Ubuntu 20.04 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 20.04 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 20.04 LTS" HOME_URL="https://www.ubuntu.com/" SUPPORT_URL="https://help.ubuntu.com/" BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/" PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy" UBUNTU_CODENAME=focal


!!DMI Information
!!---------------

Manufacturer:      Gigabyte Technology Co., Ltd.
Product Name:      B360M H
Product Version:   Default string
Firmware Version:  F3
Board Vendor:      Gigabyte Technology Co., Ltd.
Board Name:        B360M H


!!ACPI Device Status Information
!!---------------

/sys/bus/acpi/devices/ACPI000C:00/status 	 15
/sys/bus/acpi/devices/INT33A1:00/status 	 15
/sys/bus/acpi/devices/INT340E:00/status 	 15
/sys/bus/acpi/devices/INT3450:00/status 	 15
/sys/bus/acpi/devices/INT3F0D:00/status 	 15
/sys/bus/acpi/devices/LNXPOWER:00/status 	 15
/sys/bus/acpi/devices/LNXPOWER:02/status 	 1
/sys/bus/acpi/devices/LNXPOWER:03/status 	 1
/sys/bus/acpi/devices/LNXPOWER:04/status 	 1
/sys/bus/acpi/devices/LNXPOWER:05/status 	 1
/sys/bus/acpi/devices/LNXPOWER:06/status 	 1
/sys/bus/acpi/devices/LNXPOWER:07/status 	 1
/sys/bus/acpi/devices/LNXTHERM:00/status 	 11
/sys/bus/acpi/devices/PNP0103:00/status 	 15
/sys/bus/acpi/devices/PNP0501:00/status 	 15
/sys/bus/acpi/devices/PNP0C02:03/status 	 3
/sys/bus/acpi/devices/PNP0C02:05/status 	 3
/sys/bus/acpi/devices/PNP0C04:00/status 	 31
/sys/bus/acpi/devices/PNP0C0C:00/status 	 15
/sys/bus/acpi/devices/PNP0C0E:00/status 	 11
/sys/bus/acpi/devices/PNP0C0F:00/status 	 11
/sys/bus/acpi/devices/PNP0C0F:01/status 	 11
/sys/bus/acpi/devices/PNP0C0F:02/status 	 11
/sys/bus/acpi/devices/PNP0C0F:03/status 	 11
/sys/bus/acpi/devices/PNP0C0F:04/status 	 11
/sys/bus/acpi/devices/PNP0C0F:05/status 	 11
/sys/bus/acpi/devices/PNP0C0F:06/status 	 11
/sys/bus/acpi/devices/PNP0C0F:07/status 	 11
/sys/bus/acpi/devices/PNP0C14:02/status 	 11
/sys/bus/acpi/devices/PRP00001:00/status 	 11


!!Kernel Information
!!------------------

Kernel release:    5.4.0-37-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.2.2
Utilities version:  1.2.2


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------



!!PCI Soundcards installed in the system
!!--------------------------------------



!!Modprobe options (Sound related)
!!--------------------------------

snd_pcsp: index=-2
snd_usb_audio: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
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

crw-rw----  1 root audio 116,  1 Jun 22 17:15 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Jun 22 17:15 /dev/snd/timer


!!Aplay/Arecord output
!!--------------------

APLAY

aplay: device_list:274: no soundcards found...

ARECORD

arecord: device_list:274: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!--------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

acpi_pad
aesni_intel
ahci
arp_tables
aufs
autofs4
binfmt_misc
bpfilter
br_netfilter
bridge
coretemp
crc32_pclmul
crct10dif_pclmul
cryptd
crypto_simd
drm
drm_kms_helper
fb_sys_fops
ghash_clmulni_intel
glue_helper
hid
hid_generic
hid_logitech_dj
hid_logitech_hidpp
i2c_algo_bit
i2c_i801
i915
ie31200_edac
input_leds
intel_cstate
intel_pch_thermal
intel_powerclamp
intel_rapl_common
intel_rapl_msr
intel_rapl_perf
ip6_tables
ip6table_filter
ip_tables
iptable_filter
iptable_nat
joydev
kvm
kvm_intel
libahci
libcrc32c
llc
lp
mac_hid
mei
mei_hdcp
mei_me
nf_conntrack
nf_defrag_ipv4
nf_defrag_ipv6
nf_nat
nfnetlink
nls_iso8859_1
overlay
parport
parport_pc
pinctrl_cannonlake
pinctrl_intel
ppdev
r8169
realtek
sch_fq_codel
stp
syscopyarea
sysfillrect
sysimgblt
usbhid
video
wmi
wmi_bmof
x86_pkg_temp_thermal
x_tables
xfrm_algo
xfrm_user
xt_MASQUERADE
xt_addrtype
xt_conntrack


!!ALSA/HDA dmesg
!!--------------

[    0.120219] ACPI: Added _OSI(Linux-Dell-Video)
[    0.120221] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[    0.120221] ACPI: Added _OSI(Linux-HPI-Hybrid-Graphics)


!!Packages installed
!!--------------------

ii  alsa-tools                                    1.1.7-1ubuntu1                        amd64        Console based ALSA utilities for specific hardware
ii  alsa-topology-conf                            1.2.2-1                               all          ALSA topology configuration files
ii  alsa-ucm-conf                                 1.2.2-1ubuntu0.1                      all          ALSA Use Case Manager configuration files
ii  alsa-utils                                    1.2.2-1ubuntu1                        amd64        Utilities for configuring and using ALSA




---

### Post by osirus83 on 2020-06-22
My soundcard is onboard on this mobo:
[https://www.gigabyte.com/nl/Motherboard/B360M-H-rev-10#kf](https://www.gigabyte.com/nl/Motherboard/B360M-H-rev-10#kf)

---

### Post by Yellow Pasque on 2020-06-22
```
!!PCI Soundcards installed in the system
!!--------------------------------------
<blank>
```

It doesn't even show up in lspci. I would go into the BIOS, disable the 'Audio Controller' (under 'Chipset' menu), save and reboot. Then I would go back into the BIOS, and re-enable the Audio Controller. 

If that doesn't work, you may want to try resetting the BIOS. Also, I should point out that your BIOS version F3 is relatively old. If you upgrade, it will probably reset the BIOS for you. At least, my Gigabyte mobo does.

---

### Post by osirus83 on 2020-06-22
That helped, at least it brings me another step forward. At least now the sound card is found again.
[http://alsa-project.org/db/?f=3340ecbe127c6354387d8da5d2e1d8683cbcba24](http://alsa-project.org/db/?f=3340ecbe127c6354387d8da5d2e1d8683cbcba24)
And in the settings menu "dummy output" changed to "line out - internal sound"

Also executed alsamixer and unmuted all the options.

The sound is still gone though. Trying if another reboot helps.

---

### Post by osirus83 on 2020-06-22
Well, this is strange... 

In once I noticed a system sound. But sound test did nothing. No sound. Nada.
So I tried. Spotify works. I can hear my music.

But the sound test of Linux still doesn't do anything :p

Edit: solved, missed the libcanberra-pulse package[FONT=Consolas][COLOR=#242729].[/COLOR][/FONT]

---

