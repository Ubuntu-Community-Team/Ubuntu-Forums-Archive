---
title: "Sony VGN-FZ140QE wireless problem"
date: 2008-10-01
forum: Hardware
---

### Post by RickyDee on 2008-10-01
Since yesterday and sometimes before I am having troubles with my wiresless network card. It seems that the driver is not loaded for some reason. Wired network works perfectly tho. Have any idea ?

Here's the output I've got suggested:

```
ricky@moggle:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"
```
```
ricky@moggle:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 05ca:1837 Ricoh Co., Ltd 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```
```
ricky@moggle:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
08:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 16)
09:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
09:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
09:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
```
```
ricky@moggle:~$ lsmod
Module                  Size  Used by
af_packet              21636  2 
usbhid                 30720  0 
hid                    36480  1 usbhid
i915                   31360  2 
drm                    80660  3 i915
ipv6                  255172  25 
binfmt_misc            11272  1 
rfcomm                 39188  2 
l2cap                  23300  13 rfcomm
bluetooth              56964  4 rfcomm,l2cap
vboxdrv                42160  0 
sonypi                 22408  0 
ppdev                   9348  0 
acpi_cpufreq            7820  1 
cpufreq_userspace       4120  0 
cpufreq_ondemand        8084  1 
cpufreq_stats           5124  0 
freq_table              4484  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       1792  0 
cpufreq_conservative     7200  0 
dock                   10124  0 
container               4736  0 
sbs                    14216  0 
sbshc                   6784  1 sbs
nls_cp437               5760  0 
cifs                  230256  0 
iptable_filter          2944  0 
ip_tables              13000  1 iptable_filter
x_tables               14852  1 ip_tables
sbp2                   22920  0 
parport_pc             35108  0 
lp                     11332  0 
parport                35912  3 ppdev,parport_pc,lp
joydev                 11840  0 
pcmcia                 39852  0 
rtc                    13212  0 
evdev                  11776  10 
psmouse                39056  0 
serio_raw               7044  0 
sky2                   45444  0 
sony_laptop            34512  0 
video                  18832  0 
output                  3712  1 video
tifm_7xx1               7680  0 
pcspkr                  3072  0 
tifm_core               9748  1 tifm_7xx1
yenta_socket           26380  1 
rsrc_nonstatic         12800  1 yenta_socket
pcmcia_core            39440  3 pcmcia,yenta_socket,rsrc_nonstatic
button                  8336  0 
battery                13316  0 
ac                      6020  0 
shpchp                 33428  0 
pci_hotplug            29728  1 shpchp
iTCO_wdt               11808  0 
iTCO_vendor_support     3972  1 iTCO_wdt
intel_agp              24596  1 
agpgart                33328  3 drm,intel_agp
ext3                  132872  1 
jbd                    43028  1 ext3
mbcache                 8192  1 ext3
sd_mod                 29584  3 
sg                     36256  0 
sr_mod                 16804  0 
cdrom                  36512  1 sr_mod
pata_acpi               7424  0 
ata_generic             7428  0 
ahci                   27396  2 
ata_piix               18692  0 
ohci1394               32688  0 
libata                159728  4 pata_acpi,ata_generic,ahci,ata_piix
scsi_mod              151180  5 sbp2,sd_mod,sg,sr_mod,libata
ieee1394               92216  2 sbp2,ohci1394
ehci_hcd               36748  0 
uhci_hcd               25616  0 
usbcore               143724  4 usbhid,ehci_hcd,uhci_hcd
thermal                15772  0 
processor              28080  3 acpi_cpufreq,thermal
fan                     4740  0 
fbcon                  41888  0 
tileblit                2560  1 fbcon
font                    8576  1 fbcon
bitblit                 5888  1 fbcon
softcursor              2176  1 bitblit
fuse                   48404  3
```
```
ricky@moggle:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```
```
ricky@moggle:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:a9:c0:73:15  
          inet addr:192.168.0.107  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:a9ff:fec0:7315/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39286 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30831 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18429592 (17.5 MB)  TX bytes:7836055 (7.4 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1802 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:128292 (125.2 KB)  TX bytes:128292 (125.2 KB)
```
```
ricky@moggle:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```
```
ricky@moggle:~$ uname -r -m
2.6.24-19-386 i686
```
```
ricky@moggle:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
```
```
ricky@moggle:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 ----------------------------------------------------------------
  NM Path:           /org/freedesktop/NetworkManager/Devices/eth0
  Type:              Wired
  Driver:            sky2
  Active:            yes
  HW Address:        00:13:A9:C0:73:15

  Capabilities:
    Supported:       yes
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Settings
    Hardware Link:   yes

  IP Settings:
    IP Address:      192.168.0.107
    Subnet Mask:     255.255.255.0
    Broadcast:       192.168.0.255
    Gateway:         192.168.0.1
    Primary DNS:     192.168.0.1
    Secondary DNS:   0.0.0.0
```

---

### Post by pihhan on 2008-10-01
make sure you have linux-backports-modules-hardy-i386 package installed. try also loading from terminal by hand, if module is present and failed only autoload, or is not there anyway.

sudo modprobe iwl4965

then 
tail|dmesg

to see if something interesting happened.

---

### Post by RickyDee on 2008-10-01
Nice ! everything is resolved.

One thing I don't catch is ... why exactly have I had this difficulty ? I mean, my wireless adapter was working before and all of a sudden stopped working ? (Is it possible that installing drivers for VirtualBox created a conflict ?)

---

