---
title: "Asus laptop wireless does not work"
date: 2013-03-27
forum: Hardware
---

### Post by outlimits on 2013-03-27
Hello I have a asus laptop wireless does not work tried many different things. It says it is hardblocked. The fn-f2 switch does not fix it tried rfkill unblock does not work bios has no setting in it kind of lost. I ran the script wireles info here are the details.


*************** info trace ****************



**** uname -a ****


Linux ubuntu-business 3.2.0-39-generic #62-Ubuntu SMP Thu Feb 28 00:28:53 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"


**** lspci ****


03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
	Kernel driver in use: ath9k
--
08:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8131 Gigabit Ethernet [1969:1063] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1820]
	Kernel driver in use: atl1c


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 03f0:1017 Hewlett-Packard LaserJet 1300
Bus 001 Device 003: ID 13d3:5122 IMC Networks 
Bus 002 Device 003: ID 0409:55ab NEC Corp. Hub [iMac/iTouch kbd]
Bus 002 Device 004: ID 03ee:6408 Mitsumi 


**** iwconfig ****


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


**** rfkill ****


1: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: yes


**** lsmod ****


Module                  Size  Used by
iwlwifi               401140  0 
ath9k                 132428  0 
snd_hda_codec_hdmi     32474  1 
joydev                 17693  0 
snd_hda_codec_realtek   224173  1 
arc4                   12529  2 
snd_hda_intel          33719  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
radeon                808704  3 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
mac80211              506862  2 iwlwifi,ath9k
ttm                    76949  1 radeon
drm_kms_helper         46978  1 radeon
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
dm_multipath           23275  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
usbhid                 47238  0 
hid                    99636  1 usbhid
i7core_edac            28102  0 
edac_core              53746  1 i7core_edac
usblp                  18307  0 
psmouse                97485  0 
serio_raw              13211  0 
video                  19651  0 
ath9k_common           14053  1 ath9k
ath9k_hw              411239  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              205774  4 iwlwifi,ath9k,mac80211,ath
snd                    79041  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mei                    41616  0 
soundcore              15091  1 snd
asus_laptop            24493  0 
sparse_keymap          13890  1 asus_laptop
input_polldev          13896  1 asus_laptop
mac_hid                13253  0 
drm                   241971  5 radeon,ttm,drm_kms_helper
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 radeon
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180153  10 rfcomm,bnep
lp                     17799  0 
binfmt_misc            17540  1 
parport                46562  3 parport_pc,ppdev,lp
atl1c                  41718  0 
dm_raid45              78155  0 
xor                    12894  1 dm_raid45
dm_mirror              22203  0 
dm_region_hash         20961  1 dm_mirror
dm_log                 18564  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 653005  0 
zlib_deflate           27139  1 btrfs
libcrc32c              12644  1 btrfs


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.29
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1




**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****



[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****




**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
#
#                                       m   
#  mmmm   m   m  mmmm   mmmm    mmm   mm#mm 
#  #" "#  #   #  #" "#  #" "#  #"  #    #   
#  #   #  #   #  #   #  #   #  #""""    #   
#  ##m#"  "mm"#  ##m#"  ##m#"  "#mm"    "mm 
#  #             #      #                   
#  "             "      "                   
# This file is managed by puppet.  Do not make local changes.

domain buildd
nameserver 10.122.37.1


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


[    1.284906] pci 0000:00:1c.1: [8086:3b44] type 1 class 0x000604
[    1.785521] pciehp 0000:00:1c.1:pcie04: HPC vendor_id 8086 device_id 3b44 ss_vid 1043 ss_did 1c77
[    4.184479] device-mapper: multipath: version 1.3.0 loaded
[    4.201213] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.201235] ath9k 0000:03:00.0: setting latency timer to 64
[    4.258442] ath: EEPROM regdomain: 0x60
[    4.258446] ath: EEPROM indicates we should expect a direct regpair map
[    4.258451] ath: Country alpha2 being used: 00
[    4.258454] ath: Regpair used: 0x60
[    4.310766] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[    4.311514] Registered led device: ath9k-phy0
[    4.509380] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    5.240962] ath9k 0000:03:00.0: PCI INT A disabled
[    5.240989] ath9k: Driver unloaded
[    5.247532] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    5.247554] ath9k 0000:03:00.0: setting latency timer to 64
[    5.299462] ath: EEPROM regdomain: 0x60
[    5.299464] ath: EEPROM indicates we should expect a direct regpair map
[    5.299467] ath: Country alpha2 being used: 00
[    5.299468] ath: Regpair used: 0x60
[    5.301761] ieee80211 phy1: Selected rate control algorithm 'ath9k_rate_control'
[    5.302424] Registered led device: ath9k-phy1
[    5.715455] ADDRCONF(NETDEV_UP): wlan0: link is not ready


**************** done ********************

---

