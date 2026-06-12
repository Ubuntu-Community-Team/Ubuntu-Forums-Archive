---
title: "Wine sound and Wi-Fi in 10.10 doesn't work"
date: 2011-04-10
forum: Hardware
---

### Post by Asaru on 2011-04-10
Hi,
I installed Ubuntu 10.04 in August 2010. It was working fine, until I upgraded it to 10.10 about 3 days ago. Everything is fine except two things.
First, when I use any application under Wine, the sound stopped working (it worked before in 10.04). 
Second, worse issue I have now is that when I plug off my power adapter and when I start using my laptop on battery, my Wi-Fi stops working and to make it working again, I must plug it in electricity and restart whole system.
If you need any information about my hardware or software, I may post it here.
Thank You
Asaru

---

### Post by DanneStrat on 2011-04-10
> **Asaru said:**
> Hi,
I installed Ubuntu 10.04 in August 2010. It was working fine, until I upgraded it to 10.10 about 3 days ago. Everything is fine except two things.
First, when I use any application under Wine, the sound stopped working (it worked before in 10.04). 
Second, worse issue I have now is that when I plug off my power adapter and when I start using my laptop on battery, my Wi-Fi stops working and to make it working again, I must plug it in electricity and restart whole system.
If you need any information about my hardware or software, I may post it here.
Thank You
Asaru

Hi.

For your sound problem, launch wine and go into preferences

and on the "audio" tab, make sure you have "alsa" selected.

---

### Post by Asaru on 2011-04-11
> **DanneStrat said:**
> Hi.

For your sound problem, launch wine and go into preferences

and on the "audio" tab, make sure you have "alsa" selected.

Thanks a lot, the upgrade probably deselected it, and I forgot to check it (it was a long time when I was setting it for the first time)


So the first part is solved. Anyone have any idea on the second part?
I found a wireless info script on this forum, if that could be any help to you, what's happening, I'm posting it here (I did "Retrieve network status information" in that script)...
```

Version: 1.1 (Development)
Po dub 11 15:07:39 CEST 2011

***********************************************************************************************
Running networking services
***********************************************************************************************
NetworkManager is running
************************************
        Ubuntu release 
************************************

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

************************************
        Kernel
************************************

Linux asaru-laptop 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686 GNU/Linux
************************************
          List of drivers
************************************

Module                  Size  Used by
snd_seq_dummy           1350  0 
aes_i586                7280  1567 
aes_generic            26875  1 aes_i586
rfcomm                 33811  8 
binfmt_misc             6599  1 
sco                     7998  2 
bnep                    9542  2 
l2cap                  37008  16 rfcomm,bnep
parport_pc             26058  0 
ppdev                   5556  0 
dm_crypt               11385  0 
btusb                  10969  2 
bluetooth              50500  9 rfcomm,sco,bnep,l2cap,btusb
snd_hda_codec_atihdmi     2411  1 
snd_hda_codec_idt      54919  1 
joydev                  8767  0 
snd_hda_intel          22235  2 
arc4                    1165  2 
snd_hda_codec          87552  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  4 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
b43                   168681  0 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              231959  1 b43
r852                    9536  0 
sm_common               3285  1 r852
nand                   34905  2 r852,sm_common
nand_ids                2903  1 nand
fglrx                2252513  133 
nand_ecc                3938  1 nand
dell_wmi                2852  0 
cfg80211              144694  2 b43,mac80211
mtd                    18877  2 sm_common,nand
snd                    49038  14 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               55847  0 
dell_laptop             5730  0 
dcdbas                  5402  1 dell_laptop
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
psmouse                59033  0 
serio_raw               4022  0 
soundcore                880  1 snd
lp                      7342  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
sdhci_pci               6601  0 
sdhci                  15922  1 sdhci_pci
led_class               2633  2 b43,sdhci
firewire_ohci          21234  0 
ahci                   19198  3 
intel_agp              26566  0 
video                  18712  0 
firewire_core          46643  1 firewire_ohci
output                  1883  1 video
crc_itu_t               1383  1 firewire_core
tg3                   123310  0 
libahci                21728  1 ahci
ssb                    39320  1 b43
agpgart                32011  2 fglrx,intel_agp

************************************
        pci wireless devices
************************************

	Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

************************************
        usb wireless devices
************************************

Bus 003 Device 005: ID 413c:8156 Dell Computer Corp. Wireless 370 Bluetooth Mini-card

************************************
        List of network devices
************************************

  *-network
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f6cfc000-f6cfffff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 10
       serial: 00:21:70:84:dd:e2
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 firmware=sb v2.09 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:49 memory:f69f0000-f69fffff
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:5f:14:42:d6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-28-generic firmware=N/A ip=10.0.0.2 link=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1
       description: Ethernet interface
       physical id: 3
       logical name: ham0
       serial: 3e:3b:eb:46:6f:04
       size: 10MB/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full firmware=N/A ip=5.85.91.169 link=yes multicast=yes port=twisted pair speed=10MB/s


************************************
           network info
************************************

eth0      Link encap:Ethernet  HWadr 00:21:70:84:dd:e2  
          AKTIVOVÁNO V&#352;ESM&#282;ROVÉ_VYSÍLÁNÍ MULTICAST  MTU:1500  Metrika:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          kolizí:0 délka odchozí fronty:1000 
          P&#345;ijato bajt&#367;: 0 (0.0 B) Odesláno bajt&#367;: 0 (0.0 B)
          P&#345;eru&#353;ení:17 

ham0      Link encap:Ethernet  HWadr 3e:3b:eb:46:6f:04  
          inet adr:5.85.91.169  V&#353;esm&#283;r:5.255.255.255  Maska:255.0.0.0
          AKTIVOVÁNO V&#352;ESM&#282;ROVÉ_VYSÍLÁNÍ B&#282;&#381;Í MULTICAST  MTU:1200  Metrika:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          kolizí:0 délka odchozí fronty:500 
          P&#345;ijato bajt&#367;: 0 (0.0 B) Odesláno bajt&#367;: 2167 (2.1 KB)

lo        Link encap:Místní smy&#269;ka  
          inet adr:127.0.0.1  Maska:255.0.0.0
          inet6-adr: ::1/128 Rozsah:Po&#269;íta&#269;
          AKTIVOVÁNO SMY&#268;KA B&#282;&#381;Í  MTU:16436  Metrika:1
          RX packets:154 errors:0 dropped:0 overruns:0 frame:0
          TX packets:154 errors:0 dropped:0 overruns:0 carrier:0
          kolizí:0 délka odchozí fronty:0 
          P&#345;ijato bajt&#367;: 31505 (31.5 KB) Odesláno bajt&#367;: 31505 (31.5 KB)

wlan0     Link encap:Ethernet  HWadr 00:22:5f:14:42:d6  
          inet adr:10.0.0.2  V&#353;esm&#283;r:10.0.0.255  Maska:255.255.255.0
          inet6-adr: fe80::222:5fff:fe14:42d6/64 Rozsah:Linka
          AKTIVOVÁNO V&#352;ESM&#282;ROVÉ_VYSÍLÁNÍ B&#282;&#381;Í MULTICAST  MTU:1500  Metrika:1
          RX packets:53239 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36229 errors:0 dropped:0 overruns:0 carrier:0
          kolizí:0 délka odchozí fronty:1000 
          P&#345;ijato bajt&#367;: 75047494 (75.0 MB) Odesláno bajt&#367;: 4230856 (4.2 MB)


************************************
 Wireless specific network info
************************************

lo        no wireless extensions.

eth0      no wireless extensions.

ham0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Staruch"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 50:67:F0:7F:C8:C0   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

************************************
 Rfkill Blocks
************************************

0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

************************************

*************************************************************************
interfaces
*************************************************************************
auto lo
iface lo inet loopback


**************************************************************************
resolv.conf
**************************************************************************
# Generated by NetworkManager
nameserver 10.0.0.138

**************************************************************************
Modules file
**************************************************************************
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

*************************************************************************
Blacklist file
*************************************************************************
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

**************************************************************************
Files in folder /etc/modprobe.d/*
**************************************************************************
/etc/modprobe.d/alsa-base.conf
/etc/modprobe.d/blacklist-ath_pci.conf
/etc/modprobe.d/blacklist.conf
/etc/modprobe.d/blacklist-firewire.conf
/etc/modprobe.d/blacklist-framebuffer.conf
/etc/modprobe.d/blacklist-local.conf
/etc/modprobe.d/blacklist-modem.conf
/etc/modprobe.d/blacklist-oss.conf
/etc/modprobe.d/blacklist-watchdog.conf
/etc/modprobe.d/fglrx.conf
/etc/modprobe.d/intel-5300-iwlagn-disable11n.conf
/etc/modprobe.d/libpisock9.conf

***************************************************************************
NetworkManager.state
***************************************************************************

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

****************************************************************************
nm_applet_file
*****************************************************************************
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false


***************************************************************************
Route info
***************************************************************************
Sm&#283;rovací tabulka v jádru pro IP
Adresát         Brána           Maska           P&#345;ízn Metrik Odkaz  U&#382;t Rozhraní
10.0.0.0        0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
5.0.0.0         0.0.0.0         255.0.0.0       U     0      0        0 ham0
0.0.0.0         10.0.0.138      0.0.0.0         UG    0      0        0 wlan0

******************************************************************************
Using nm-tool
******************************************************************************

NetworkManager Tool

State: connected

- Device: wlan0  [*******] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connected
  Default:           yes
  HW Address:        00:22:5F:14:42:D6

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Staruch:        Infra, 50:67:F0:7F:C8:C0, Freq 2442 MHz, Rate 54 Mb/s, Strength 54 WPA

  IPv4 Settings:
    Address:         10.0.0.2
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.138

    DNS:             10.0.0.138


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        00:21:70:84:DD:E2

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



******************************************************************************
Using iwlist scan
******************************************************************************
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ham0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 50:67:F0:7F:C8:C0
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"*******"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000274fcb21ea
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 000753746172756368
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1607070300000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050001087A12
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706435A20010D10
                    IE: Unknown: DD1E00904C336E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3407070300000000000000000000000000000000000000

Finished <<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<


```

---

