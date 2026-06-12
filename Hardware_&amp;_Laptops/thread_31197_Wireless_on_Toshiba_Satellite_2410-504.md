---
title: "Wireless on Toshiba Satellite 2410-504"
date: 2005-05-02
forum: Hardware &amp; Laptops
---

### Post by mikemoate on 2005-05-02
Apologies if the information I need has been posted before but I have searched alot and cannot find it.

I have a Toshiba Satellite 2410-504 laptop with a Toshiba Mini PCI Wireless LAN card. The laptop dual boots WinXP and Ubuntu Hoary.

 Ubuntu seems to have picked up the card and set-up the appropriate modules but try as I might I cannot get the card working even with WEP turned off on the router. The router is a D-Link DSL-604+ and it works fine with my laptops card using 128bit WEP under WinXP.

The following is all the info I can collect that may help:

output of dmesg (trimmed):
```

orinoco 0.13e (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
orinoco_cs 0.13e (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
eth1: Station identity 001f:0001:0008:000a
eth1: Looks like a Lucent/Agere firmware version 8.10
eth1: Ad-hoc demo mode supported
eth1: IEEE standard IBSS ad-hoc mode supported
eth1: WEP supported, 104-bit key
eth1: MAC address 00:02:2D:6F:A2:8C
eth1: Station name "HERMES I"
eth1: ready
eth1: index 0x01: Vcc 3.3, irq 11, io 0x0100-0x013f
acpi-cpufreq: CPU0 - ACPI performance management activated.
eth0: no IPv6 routers present
eth1: no IPv6 routers present
eth1: no IPv6 routers present
eth1: no IPv6 routers present
eth1: New link status: Disconnected (0002)
input: AT Translated Set 2 keyboard on isa0060/serio0
input: AT Translated Set 2 keyboard on isa0060/serio0

```

output of lsmod:
```

Module                  Size  Used by
acpi_cpufreq            5892  1
speedstep_lib           4228  0
proc_intf               4100  0
freq_table              4100  1 acpi_cpufreq
cpufreq_userspace       4572  1
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
orinoco_cs              8968  1
orinoco                38284  1 orinoco_cs
hermes                  7936  2 orinoco_cs,orinoco
pcmcia                 21380  7 orinoco_cs
video                  16260  0
toshiba_acpi            9388  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
ipv6                  229504  9
af_packet              20744  6
yenta_socket           19584  1
pcmcia_core            53568  3 orinoco_cs,pcmcia,yenta_socket
e100                   32384  0
mii                     4736  1 e100
ohci1394               31876  0
snd_intel8x0           29984  2
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
uhci_hcd               30224  0
usbcore               107384  2 uhci_hcd
pci_hotplug            30512  0
intel_agp              20636  1
agpgart                31784  1 intel_agp
floppy                 54864  0
rtc                    12216  0
pcspkr                  3816  0
nls_iso8859_1           4224  1
nls_cp437               5888  1
vfat                   12928  1
fat                    37792  1 vfat
md                     43856  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
evdev                   9088  0
tsdev                   7488  0
sr_mod                 16036  0
sbp2                   22408  0
scsi_mod              119936  2 sr_mod,sbp2
ieee1394              100408  2 ohci1394,sbp2
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  2 sr_mod,ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
piix                    9988  1
ide_disk               18176  4
ide_core              118988  4 ide_cd,ide_generic,piix,ide_disk
unix                   26164  811
thermal                13576  0
processor              22708  2 acpi_cpufreq,thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

```

output of lspci:
```

0000:00:00.0 Host bridge: Intel Corp. 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #1) (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #2) (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corp. 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801CAM IDE U100 (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801CA/CAM AC'97 Audio Controller (rev 02)
0000:00:1f.6 Modem: Intel Corp. 82801CA/CAM AC'97 Modem Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go] (rev a3)
0000:02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:02:08.0 Ethernet controller: Intel Corp. 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
0000:02:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
0000:02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 32)
0000:02:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 32)
0000:02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)

```

output of cardctl info 0:
```

PRODID_1="TOSHIBA"
PRODID_2="Wireless LAN Card"
PRODID_3="Version 01.01"
PRODID_4=""
MANFID=0156,0002
FUNCID=6

```

output of iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"bananas"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 44:44:44:44:44:44
          Bit Rate:2 Mb/s   Tx-Power=15 dBm   Sensitivity:1/3
          Retry limit:4   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
(The Access Point MAC Address is obviously wrong)

output of ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:00:39:F5:44:DC
          inet addr:192.168.0.132  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::200:39ff:fef5:44dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1587 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1549 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1241832 (1.1 MiB)  TX bytes:265885 (259.6 KiB)

eth1      Link encap:Ethernet  HWaddr 00:02:2D:6F:A2:8C
          inet6 addr: fe80::202:2dff:fe6f:a28c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:56 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x100

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15786 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15786 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1194605 (1.1 MiB)  TX bytes:1194605 (1.1 MiB)

```

I seem to be unable to set the card to the correct channel for the access point. iwconfig eth1 channel 6 gives the following:

Error for wireless request "Set Frequency" (8B04) :
    SET failed on device eth1 ; Operation not supported.

Additionally iwlist eth1 scanning gives:

eth1      Interface doesn't support scanning : Operation not supported


Any help/suggestions on how to get Wireless working would be appreciated, this is a major obstacle to me using ubuntu.

Mike

---

