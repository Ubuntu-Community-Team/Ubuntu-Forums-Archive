---
title: "Acer Aspire One D257 w/ 10.04 Lucid: Wi-Fi disabled"
date: 2012-08-17
forum: Hardware
---

### Post by Rafu on 2012-08-17
My girlfriend was bought by her mom an Acer Aspire One D257 netbook, which comes with Windows 7.
We installed Ubuntu 10.04 LTS Lucid (which is what we use on all our computers) on it, as a dual-boot option. However, Wi-Fi is disabled by default and it's not possible to turn it on via keyboard shortcut. We're apparently not tech-savvy enough to have a clue what to do.
Wi-Fi appears to work normally when booting with Windows, but no way we're connecting a Windows system to the Internet (and risk an epidemic of malware)! When booting with Ubuntu, ethernet cable connection works fine and we've been using it to update the system sometimes.

---

### Post by unevenflow on 2012-08-17
Hey, open terminal and type

```
lshw -C network
```

and post back the results

---

### Post by Rafu on 2012-08-17
> **unevenflow said:**
> Hey, open terminal and type

```
lshw -C network
```and post back the results

Done. Here are the results:
```
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: e8:9a:8f:c1:1f:77
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:28 ioport:3000(size=256) memory:50004000-50004fff(prefetchable) memory:50000000-50003fff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:54000000-54001fff
```

---

### Post by unevenflow on 2012-08-17
please do this and again post back

[http://ubuntuforums.org/showpost.php?p=12177215&postcount=5](http://ubuntuforums.org/showpost.php?p=12177215&postcount=5)

---

### Post by Rafu on 2012-08-17
Here you are:

```

*************** info trace ****************



**** uname -a ****


Linux brutto-anatroccolo 2.6.32-41-generic #89-Ubuntu SMP Fri Apr 27 22:22:09 UTC 2012 i686 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"


**** lspci ****


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Kernel driver in use: r8169
    Kernel modules: r8169
02:00.0 Network controller [0280]: Intel Corporation Device [8086:08ae]
03:00.0 Class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)


**** lsusb ****


Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0402:7675 ALi Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


**** iwconfig ****




**** rfkill ****




**** lsmod ****


Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203472  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8740  0 
snd_hda_intel          22069  2 
snd_hda_codec          74297  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  290035  3 
drm_kms_helper         29329  1 i915
uvcvideo               57438  0 
led_class               2864  0 
drm                   163779  4 i915,drm_kms_helper
soundcore               6620  1 snd
videodev               34457  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
psmouse                63677  0 
serio_raw               3978  0 
intel_agp              24375  2 i915
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 drm,intel_agp
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
ahci                   32680  2 
r8169                  34140  0 
mii                     4381  1 r8169


**** nm-tool ****



NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.86
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1




**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


**** NetworkManager.conf ****




**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****




**** resolv ****


# Generated by NetworkManager
domain homenet.telecomitalia.it
search homenet.telecomitalia.it
nameserver 192.168.1.1


**** blacklist.conf ****


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


**** dmesg ****


[    0.614318] device-mapper: multipath: version 1.1.0 loaded
[    0.614331] device-mapper: multipath round-robin: version 1.0.0 loaded
[   14.594289] acer-wmi: Acer Laptop ACPI-WMI Extras
[   14.594316] acer-wmi: No or unsupported WMI interface, unable to load


**************** done ********************
```

---

### Post by unevenflow on 2012-08-17
Download this 
[http://packages.ubuntu.com/oneiric/all/linux-firmware/download](http://packages.ubuntu.com/oneiric/all/linux-firmware/download)
right click and open with gdebi
then reboot and see if it works.

---

### Post by Rafu on 2012-08-17
> **unevenflow said:**
> then reboot and see if it works.
It doesn't appear to work. :(

---

### Post by unevenflow on 2012-08-17
Please try in terminal 

```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

### Post by Rafu on 2012-08-19
> **unevenflow said:**
> Please try in terminal 

```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

First command echoes:
```
options iwlwifi 11n_disable=1
```
(no further result).

Both second and third command result in this output:
```
FATAL: Module iwlwifi not found.
```

I have no idea what that means, of course. Do you?

---

### Post by gleble on 2013-01-19
I have the same problem with a new install of 10.04 on an Acer one happy
I followed all the steps above an end up with this
FATAL: Module iwlwifi not found.
Does anyone understand/know how to fix this.

---

### Post by oxf on 2013-01-19
> **gleble said:**
> I have the same problem with a new install of 10.04 on an Acer one happy
I followed all the steps above an end up with this
FATAL: Module iwlwifi not found.
Does anyone understand/know how to fix this.

I have an Acer Aspire One with 12.04 LTS on and it works perfectly. Maybe try that?

Caitlin

---

### Post by gleble on 2013-01-19
I don't like 12.04. The Acer used to have wifi with 10.04

---

