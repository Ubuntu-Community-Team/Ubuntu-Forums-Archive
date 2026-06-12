---
title: "Wifi enable"
date: 2012-06-03
forum: Hardware
---

### Post by AlexMrKlim on 2012-06-03
Hi All !

Some times ago, I had Ubuntu (unity), and my wifi worked correctly.
Yesterday, I installed XUbuntu (xfse). In the "Settings -> Additional Drivers" I don't see driver for wifi. 

How I can enable wifi \ install driver or something else ? 

```

$ lsusb 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 064e:c107 Suyin Corp. HP webcam [dv6-1190en]
Bus 006 Device 002: ID 138a:0001 Validity Sensors, Inc. VFS101 Fingerprint Reader
Bus 007 Device 002: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]

```

```

$ lsusb -t
6-1:1.0: No such file or directory
7-2:1.2: No such file or directory
7-2:1.3: No such file or directory
/:  Bus 08.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 2: Dev 2, If 0, Class='bInterfaceClass 0xe0 not yet handled', Driver=btusb, 12M
    |__ Port 2: Dev 2, If 1, Class='bInterfaceClass 0xe0 not yet handled', Driver=btusb, 12M
    |__ Port 2: Dev 2, If 2, Class=vend., Driver=, 12M
    |__ Port 2: Dev 2, If 3, Class=app., Driver=, 12M
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 1: Dev 2, If 0, Class=vend., Driver=, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/8p, 480M
    |__ Port 4: Dev 3, If 0, Class='bInterfaceClass 0x0e not yet handled', Driver=uvcvideo, 480M
    |__ Port 4: Dev 3, If 1, Class='bInterfaceClass 0x0e not yet handled', Driver=uvcvideo, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/4p, 480M

```


P.S. My PC: HP Pavilion dv5-1140ew. Bluetooth works correct.

---

### Post by shafi.dude99 on 2012-06-03
paste the output of this command to

sudo lshw -C network

lspci -nn | grep 0280

---

### Post by AlexMrKlim on 2012-06-03
```

$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:1b:57:78
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.33 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:48 ioport:6000(size=256) memory:d4010000-d4010fff memory:d4000000-d400ffff memory:d4020000-d402ffff

```

```

$ lspci -nn | grep 0280

```
--> nothing...

---

### Post by ajgreeny on 2012-06-03
No wifi adapter is detected.  Does it have  physical switch which is "off" at the moment?

---

### Post by AlexMrKlim on 2012-06-03
I have one physical switch to turn on\off both bluetooth and wifi. 
At the moment switch is on, but I can use only bluetooth.

---

### Post by Ianman on 2012-06-03
I have read that if both Bluetooth and wifi are enabled, the Bluetooth can interfere with wifi. Try disabling bluetooth.

---

### Post by AlexMrKlim on 2012-06-03
Sorry.. 
How can I turn off bluetooth ?
And I think, that I should install driver for wifi too. Or not ?

---

### Post by josephmills on 2012-06-03
can we see a ```
rfkill list all 
```

and a ```
lspci -nn && lsmod
```
thanks

---

### Post by ajgreeny on 2012-06-03
You can't install a driver for wifi when there is no way to see what driver you might need to install.

Many drivers are already included in the kernel, so disabling bluetooth may indeed be an answer, but I am not sure how you can do that if you are running 12.04.

---

### Post by AlexMrKlim on 2012-06-03
> **josephmills said:**
> can we see a ```
rfkill list all 
```

and a ```
lspci -nn && lsmod
```
thanks


Yes, sure )

1) if switch is "off":
```

0: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: yes

```

2) if switch is "on":
```

$ rfkill list all
0: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

```

$ lspci -nn && lsmod
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
00:1d.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.3 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1d.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
00:1f.6 Signal processing controller [1180]: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem [8086:2932] (rev 03)
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G96 [GeForce 9600M GT] [10de:0649] (rev a1)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
06:00.0 FireWire (IEEE 1394) [0c00]: JMicron Technology Corp. IEEE 1394 Host Controller [197b:2380]
06:00.1 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382]
06:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381]
06:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383]
06:00.4 System peripheral [0880]: JMicron Technology Corp. xD Host Controller [197b:2384]
Module                  Size  Used by
ums_cypress            12627  0 
usb_storage            39646  2 ums_cypress
uas                    17828  0 
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17830  2 
rfcomm                 38139  16 
vesafb                 13516  1 
nvidia              10958194  43 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  6 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ir_mce_kbd_decoder     12681  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ir_sony_decoder        12462  0 
uvcvideo               67203  0 
ir_jvc_decoder         12459  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17393  0 
ir_rc6_decoder         12459  0 
snd                    62064  21 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rc_rc6_mce             12454  0 
ir_rc5_decoder         12459  0 
btusb                  17912  2 
bluetooth             158438  23 bnep,rfcomm,btusb
hp_accel               25728  0 
videodev               86588  1 uvcvideo
ir_nec_decoder         12459  0 
lis3lv02d              19268  1 hp_accel
ene_ir                 18019  0 
jmb38x_ms              17406  0 
memstick               15857  1 jmb38x_ms
soundcore              14635  1 snd
psmouse                87213  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
rc_core                21263  10 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,rc_rc6_mce,ir_rc5_decoder,ir_nec_decoder,ene_ir
hp_wmi                 13652  0 
video                  19068  0 
mac_hid                13077  0 
input_polldev          13648  1 lis3lv02d
sparse_keymap          13658  1 hp_wmi
serio_raw              13027  0 
wmi                    18744  1 hp_wmi
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40180  0 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
r8169                  56321  0 

```

---

### Post by josephmills on 2012-06-04
:confused:
 I do not see a wireless card in the read out. 

is this usb ? if so can we see a 
```
lsusb
```

---

### Post by AlexMrKlim on 2012-06-04
Yep, I have wireless card on usb.
```

$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 064e:c107 Suyin Corp. HP webcam [dv6-1190en]
Bus 006 Device 002: ID 138a:0001 Validity Sensors, Inc. VFS101 Fingerprint Reader
Bus 005 Device 002: ID 04f3:02f4 Elan Microelectronics Corp. 2.4G Cordless Mouse
Bus 007 Device 002: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]

```

---

### Post by josephmills on 2012-06-04
I am stumped and also not Bluetooth kinda person sorry. Good luck.

---

