---
title: "Bluetooth USB Adapter and Edgy"
date: 2007-01-26
forum: Hardware &amp; Laptops
---

### Post by fogNL on 2007-01-26
I recently purchased a Bluetooth USB adapter so I can interface my Nokia phone with my Acer laptop.

The brand name of the USB adapter is "Rocketfish", however, it registers as a Broadcom.  I cannot get the adapter to work, and was wondering if it was something I was doing, or if it just isn't compatible.

When I plug it in, dmesg gives me this:

```

[17290898.716000] usb 3-2: new full speed USB device using uhci_hcd and address 5
[17290898.896000] usb 3-2: configuration #1 chosen from 1 choice
[17290898.900000] hub 3-2:1.0: USB hub found
[17290898.900000] hub 3-2:1.0: 3 ports detected
[17290899.216000] usb 3-2.2: new full speed USB device using uhci_hcd and address 6
[17290899.360000] usb 3-2.2: configuration #1 chosen from 1 choice
[17290899.364000] input: Broadcom Corp BCM2045B3 ROM as /class/input/input14
[17290899.364000] input: USB HID v1.11 Keyboard [Broadcom Corp BCM2045B3 ROM] on usb-0000:00:1d.2-2.2
[17290899.568000] usb 3-2.3: new full speed USB device using uhci_hcd and address 7
[17290899.708000] usb 3-2.3: configuration #1 chosen from 1 choice
[17290899.716000] input: Broadcom Corp BCM2045B3 ROM as /class/input/input15
[17290899.716000] input: USB HID v1.11 Mouse [Broadcom Corp BCM2045B3 ROM] on usb-0000:00:1d.2-2.3

```

lsusb output:

```

Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 007: ID 0a5c:4503 Broadcom Corp.
Bus 003 Device 006: ID 0a5c:4502 Broadcom Corp.
Bus 003 Device 005: ID 0a5c:4500 Broadcom Corp.
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 005: ID 046d:c518 Logitech, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```

lsmod output:

```

Module                  Size  Used by
vfat                   14720  0
fat                    56348  1 vfat
isofs                  38076  0
nls_cp437               6912  1
loop                   17672  0
sg                     37404  0
sd_mod                 22656  0
usb_storage            75072  0
libusual               17040  1 usb_storage
vmnet                  38060  13
parport_pc             37796  0
vmmon                 109284  0
arc4                    3200  2
ieee80211_crypt_wep     6528  1
af_packet              24584  4
ipv6                  272288  14
rfcomm                 42260  0
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
fglrx                 527152  9
speedstep_centrino      9760  1
cpufreq_userspace       5408  0
cpufreq_stats           7744  0
freq_table              6048  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       2944  0
cpufreq_ondemand        8876  1
cpufreq_conservative     8712  0
video                  17540  0
tc1100_wmi              8324  0
sbs                    16804  0
sony_acpi               6412  0
pcc_acpi               14080  0
i2c_ec                  6272  1 sbs
i2c_core               23424  1 i2c_ec
hotkey                 11556  0
dock                    8716  0
dev_acpi               12292  0
button                  7952  0
battery                11652  0
container               5632  0
ac                      6788  0
asus_acpi              17688  0
nls_utf8                3200  1
ntfs                  112116  1
sbp2                   24584  0
scsi_mod              144648  4 sg,sd_mod,usb_storage,sbp2
lp                     12964  0
parport                39496  2 parport_pc,lp
pcmcia                 40380  0
tg3                   107652  0
ipw2200               115652  0
ieee80211              35272  1 ipw2200
ieee80211_crypt         7552  2 ieee80211_crypt_wep,ieee80211
tifm_7xx1               9472  0
tifm_core              10496  1 tifm_7xx1
yenta_socket           28812  1
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
tsdev                   9152  0
joydev                 11200  0
snd_intel8x0           34844  2
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
intel_agp              26012  1
agpgart                34888  2 fglrx,intel_agp
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
psmouse                41352  0
evdev                  11392  3
shpchp                 42144  0
pci_hotplug            32828  1 shpchp
irda                  214332  0
crc_ccitt               3200  1 irda
serio_raw               8452  0
usbhid                 45152  0
ext3                  142728  2
jbd                    62228  1 ext3
ohci1394               37040  0
ieee1394              306104  2 sbp2,ohci1394
ehci_hcd               34696  0
uhci_hcd               24968  0
usbcore               134912  6 usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
ide_generic             2432  0
ide_cd                 33696  0
cdrom                  38944  1 ide_cd
ide_disk               18560  5
piix                   11780  1
generic                 6276  0
thermal                15624  0
processor              31560  2 speedstep_centrino,thermal
fan                     6020  0
fbcon                  41504  0
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0
capability              5896  0
commoncap               8704  1 capability

```

hciconfig scan output:

```

Can't get device info: No such device

```

My laptop is an Acer Aspire 1694WLMi running Edgy.

Thanks

---

### Post by Efrain Valles on 2007-02-11
Try

```
hciconfig
```

to see all bluetooth conections.
it should read UP and RUNNING :D


```

sudo hcitools scan
```

to see if you can find any devices

```

sudo hcitools
```


if you get an error like . no connection or something like that try

try restarting hciconfig
```

 sudo hciconfig hci0 reset
```

try scanning again and see if you get the thing to work:) :)

---

