---
title: "Intel Centrino Wireless-N 135 installation issues"
date: 2014-08-19
forum: Hardware
---

### Post by nick136 on 2014-08-19
Hi, this is my first post on this forum so thanks for having me.  I literally started playing about with Ubuntu yesterday, no prior experience so I am slightly unsure about things still.  Anyways, I have internet, but it appears to be wired.  What I am trying to do is get wireless working, my internal wireless card is an Intel Centrino Wireless-N 135.

So first thing I did was download iwlwifi-135-ucode-18.168.6.1 because my device was listed under this.  I then copied the whole unzipped folder into lib/firmware.  I then went into this folder, and copied the .ucode file, and I pasted this directly into lib/firmware.  I presumed this would give me wireless access.

Apparently its still not working.  I have forum experience on other forums, so I presume you will want some details.  The command cat -n /etc/apt/sources.list gives me
```

1    # 
     2    deb http://http.kali.org/ /kali main contrib non-free
     3    deb http://http.kali.org/ /wheezy main contrib non-free
     4    deb http://http.kali.org/kali kali-dev main contrib non-free
     5    deb http://http.kali.org/kali kali-dev main/debian-installer
     6    deb-src http://http.kali.org/kali kali-dev main contrib non-free
     7    deb http://http.kali.org/kali kali main contrib non-free
     8    deb http://http.kali.org/kali kali main/debian-installer
     9    deb-src http://http.kali.org/kali kali main contrib non-free
    10    deb http://security.kali.org/kali-security kali/updates main contrib non-free
    11    deb-src http://security.kali.org/kali-security kali/updates main contrib non-free
    12    # deb cdrom:[Debian GNU/Linux 7.0 _Kali_ - Official Snapshot amd64 LIVE/INSTALL Binary 20140721-22:25]/ kali contrib main non-free
    13    
    14    #deb cdrom:[Debian GNU/Linux 7.0 _Kali_ - Official Snapshot amd64 LIVE/INSTALL Binary 20140721-22:25]/ kali contrib main non-free
    15    
    16    ## Security updates

```

If I do iwlist scan I get
```

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

```

If I do lsmod I get
[HTML]Module                  Size  Used by
nls_utf8               12456  1 
isofs                  38963  1 
udf                    83758  0 
crc_itu_t              12347  1 udf
nfnetlink_log          17241  0 
nfnetlink              12989  1 nfnetlink_log
vboxsf                 37350  0 
binfmt_misc            16949  1 
rt2800pci              13100  0 
rt2800mmio             13390  1 rt2800pci
rt2800lib              77399  2 rt2800pci,rt2800mmio
rt2x00pci              12520  1 rt2800pci
rt2x00mmio             12601  2 rt2800pci,rt2800mmio
rt2x00lib              46372  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
eeprom_93cx6           12625  1 rt2800pci
mac80211              488308  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              436618  2 mac80211,rt2x00lib
crc_ccitt              12347  1 rt2800lib
rfkill                 18902  2 cfg80211
loop                   26605  0 
dm_crypt               22731  0 
vboxvideo              12437  0 
joydev                 17108  0 
drm                   240557  1 vboxvideo
vboxguest             189903  7 vboxsf
i2c_piix4              12672  0 
processor              28221  0 
i2c_core               24265  2 drm,i2c_piix4
thermal_sys            27685  1 processor
psmouse                86464  0 
serio_raw              12849  0 
snd_intel8x0           34948  2 
snd_ac97_codec        114660  1 snd_intel8x0
snd_pcm                88538  2 snd_ac97_codec,snd_intel8x0
snd_timer              26606  1 snd_pcm
snd                    61039  8 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm
parport_pc             26287  0 
parport                35699  1 parport_pc
soundcore              13026  1 snd
ac97_bus               12510  1 snd_ac97_codec
ac                     12678  0 
battery                13101  0 
button                 12944  0 
evdev                  17489  6 
ext4                  489943  1 
crc16                  12343  1 ext4
mbcache                13082  1 ext4
jbd2                   86788  1 ext4
dm_mod                 89276  1 dm_crypt
hid_generic            12393  0 
usbhid                 44481  0 
hid                    94062  2 hid_generic,usbhid
sd_mod                 44346  3 
crct10dif_generic      12581  1 
sg                     30043  0 
sr_mod                 21898  1 
crc_t10dif             12431  1 sd_mod
cdrom                  39232  1 sr_mod
crct10dif_common       12356  2 crct10dif_generic,crc_t10dif
ata_generic            12490  0 
ahci                   29195  2 
libahci                27103  1 ahci
ata_piix               33592  1 
ehci_pci               12472  0 
ohci_pci               12808  0 
ohci_hcd               34767  1 ohci_pci
ehci_hcd               48517  1 ehci_pci
libata                169163  4 ahci,libahci,ata_generic,ata_piix
usbcore               166472  5 ohci_hcd,ohci_pci,ehci_hcd,ehci_pci,usbhid
usb_common             12440  1 usbcore
e1000                 102132  0 
scsi_mod              186841  4 sg,libata,sd_mod,sr_mod

[/HTML]

So the point of this post is that I have no idea what I am doing, and I hope I have provided enough information for someone to guide me.  If I do iwconfig it says no wireless extensions for both of them.

If someone could help me that would be great.  If you need any further information let me know and I will get it to you.

Thanks

Nick

---

### Post by nick136 on 2014-08-20
Hi, I saw another thread where they requested a wireless script is run, so this is my output from this

```


########## wireless info START ##########

Report from: 19 Aug 2014 23:04 BST +0100

Script from: 17 Aug 2014 02:46 UTC +0000

##### release #####

Distributor ID:    Debian
Description:    Debian GNU/Linux Kali Linux 1.0.8
Release:    Kali Linux 1.0.8
Codename:    n/a

##### kernel #####

Linux 3.14-kali1-amd64 #1 SMP Debian 3.14.5-1kali1 (2014-06-07) x86_64 unknown unknown GNU/Linux

Parameters: ro, initrd=/install/initrd.gz, quiet

##### desktop #####

default

##### lspci #####

00:03.0 Ethernet controller [0200]: Intel Corporation 82540EM Gigabit Ethernet Controller [8086:100e] (rev 02)
    Subsystem: Intel Corporation PRO/1000 MT Desktop Adapter [8086:001e]
    Kernel driver in use: e1000

##### lsusb #####

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 80ee:0021 VirtualBox USB Tablet
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info #####

./wireless_script: line 103: pccardctl: command not found

##### rfkill #####

##### lsmod #####

rt2800pci              13100  0 
rt2800mmio             13390  1 rt2800pci
rt2800lib              77399  2 rt2800pci,rt2800mmio
rt2x00pci              12520  1 rt2800pci
rt2x00mmio             12601  2 rt2800pci,rt2800mmio
rt2x00lib              46372  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
eeprom_93cx6           12625  1 rt2800pci
mac80211              488308  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              436618  2 mac80211,rt2x00lib
crc_ccitt              12347  1 rt2800lib

##### interfaces #####

auto lo
iface lo inet loopback

allow-hotplug eth0
iface eth0 inet dhcp

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          inet addr:192.168.0.29  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe49:8ac8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40577 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7674 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56042603 (53.4 MiB)  TX bytes:627323 (612.6 KiB)

##### iwconfig #####

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

##### resolv.conf #####

domain Home
search Home
nameserver 192.168.0.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000
  State:             unmanaged
  Default:           no
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (N/A, 20)
    (2457 - 2482 @ 40), (N/A, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (N/A, 20), PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 80), (N/A, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 80), (N/A, 20), PASSIVE-SCAN, NO-IBSS
    (57240 - 63720 @ 2160), (N/A, 0)

##### iwlist channels #####

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #####

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos #####

[rt2800pci]
filename:       /lib/modules/3.14-kali1-amd64/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     D876F002AA85529257D61EB
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.14-kali1-amd64 SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800mmio]
filename:       /lib/modules/3.14-kali1-amd64/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     F196893F5F72140CA847345
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       3.14-kali1-amd64 SMP mod_unload modversions 

[rt2800lib]
filename:       /lib/modules/3.14-kali1-amd64/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     045B7E84F3DBB154C7AEC06
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.14-kali1-amd64 SMP mod_unload modversions 

[rt2x00pci]
filename:       /lib/modules/3.14-kali1-amd64/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     E940DB1895D1B7E99CD4B46
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.14-kali1-amd64 SMP mod_unload modversions 

[rt2x00mmio]
filename:       /lib/modules/3.14-kali1-amd64/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     07530604F5CE4EF69872C75
depends:        rt2x00lib
intree:         Y
vermagic:       3.14-kali1-amd64 SMP mod_unload modversions 

[rt2x00lib]
filename:       /lib/modules/3.14-kali1-amd64/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     6791C3895D6D2F5D832F327
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.14-kali1-amd64 SMP mod_unload modversions 

##### module parameters #####

[rt2800pci]
nohwcrypt: N

##### /etc/modules #####

loop
rt2800pci

##### blacklists #####

[/etc/modprobe.d/blacklist-libnfc.conf]
blacklist nfc
blacklist pn533

[/etc/modprobe.d/kali-blacklist.conf]
blacklist snd_pcsp
blacklist pcspkr

##### udev rules #####

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #####

[    0.682648] e1000: Intel(R) PRO/1000 Network Driver - version 7.3.21-k8-NAPI
[    1.060688] e1000 0000:00:03.0 eth0: Intel(R) PRO/1000 Network Connection
[    4.085041] platform microcode: firmware: direct-loading firmware intel-ucode/06-3c-03

########## wireless info END ############

```

Thanks

---

