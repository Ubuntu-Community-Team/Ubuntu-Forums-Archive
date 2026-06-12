---
title: "Hardware Problems with Ubuntu 8.10 &amp; Asus F3L Notebook"
date: 2009-03-02
forum: Hardware
---

### Post by mwhite1206 on 2009-03-02
Hi everyone,

I know there's been a lot of threads about hardware issues with Ubuntu & Asus notebooks, especially the sound & wireless cards. However, I haven't been able to find anything yet that works to fix my problems, and I'm REALLY new to Linux, so I have NO idea what needs doing :confused:. I'm running Ubuntu 8.10 on an ASUS F3L notebook.

With the sound card, all I can hear when Ubuntu tries to make noise is electronic 'clicking' coming out of the speakers, and it doesn't recognise when I plug in headphones. The wireless card appears to be automatically turned off, and whenever I go back into Windows (I'm running dual-boot until I figure out Ubuntu) I need to go in and manually switch the wireless back on (usually Windows remembers to keep it on.)

Let me know what system info you need to help out, and, more importantly, how one actually gets to said system information :p

Cheers in advance,
Marc

---

### Post by mwhite1206 on 2009-03-04
I managed to glean the following commands for system information of someone else's post, hopefully there's something useful in there....

Outcome of lspci:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
03:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
08:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
08:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

Outcome of lsusb:
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04f2:b012 Chicony Electronics Co., Ltd 1.3 MPixel UVC webcam
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Outcome of ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:13:8f:8a  
          inet addr:150.203.88.194  Bcast:150.203.91.255  Mask:255.255.252.0
          inet6 addr: fe80::21f:c6ff:fe13:8f8a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3663 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2190 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:2249643 (2.2 MB)  TX bytes:519041 (519.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

Outcome of ifconfig -a:
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:13:8f:8a  
          inet addr:150.203.88.194  Bcast:150.203.91.255  Mask:255.255.252.0
          inet6 addr: fe80::21f:c6ff:fe13:8f8a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3953 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2235 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:2366511 (2.3 MB)  TX bytes:527506 (527.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

pan0      Link encap:Ethernet  HWaddr be:dc:5d:0b:84:0c  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:7e:3a:a0  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:fe5f0000-fe600000 

Outcome of iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

Outcome of lsmod:
Module                  Size  Used by
ipv6                  263972  10 
i915                   38528  2 
drm                    86056  3 i915
binfmt_misc            16904  1 
af_packet              25728  2 
rfcomm                 44432  2 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  16 rfcomm,bnep
ppdev                  15620  0 
acpi_cpufreq           15500  1 
cpufreq_userspace      11396  0 
cpufreq_powersave       9856  0 
cpufreq_stats          13188  0 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  1 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
pci_slot               12680  0 
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
wmi                    14504  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
snd_hda_intel         384176  2 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
uvcvideo               63624  0 
psmouse                45200  0 
evdev                  17696  11 
compat_ioctl32          9344  1 uvcvideo
btusb                  19736  3 
serio_raw              13444  0 
pcspkr                 10624  0 
videodev               41344  1 uvcvideo
v4l1_compat            22404  2 uvcvideo,videodev
bluetooth              61924  11 rfcomm,sco,bnep,l2cap,btusb
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
battery                18436  0 
asus_laptop            24568  0 
ndiswrapper           196380  0 
video                  25232  0 
output                 11008  1 video
snd                    63268  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ac                     12292  0 
sdhci_pci              15360  0 
tpm_infineon           17064  0 
tpm                    22848  1 tpm_infineon
tpm_bios               14080  1 tpm
led_class              12164  1 asus_laptop
sdhci                  23940  1 sdhci_pci
button                 14224  0 
soundcore              15328  1 snd
intel_agp              33724  1 
ricoh_mmc              11904  0 
mmc_core               58268  1 sdhci
agpgart                42184  3 drm,intel_agp
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133256  4 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sd_mod                 42392  8 
crc_t10dif              9984  1 sd_mod
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sg                     39732  0 
ata_generic            12932  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
ata_piix               24580  7 
ohci1394               37936  0 
pata_acpi              12160  0 
ieee1394               96324  2 sbp2,ohci1394
libata                178208  3 ata_generic,ata_piix,pata_acpi
scsi_mod              155212  5 sbp2,sd_mod,sr_mod,sg,libata
dock                   16656  1 libata
atl1                   40968  0 
mii                    13440  1 atl1
ehci_hcd               43788  0 
uhci_hcd               30736  0 
usbcore               149360  7 uvcvideo,btusb,ndiswrapper,usbhid,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  7 

Outcome to sudo lshw -C network:
  *-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:1f:c6:13:8f:8a
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.1.3 duplex=full firmware=N/A ip=150.203.88.194 latency=0 link=yes module=atl1 multicast=yes port=twisted pair speed=1GB/s
  *-network DISABLED
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:15:af:7e:3a:a0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.53+,07/26/2007,5.3.0.67 latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: be:dc:5d:0b:84:0c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Outcome of iwlist scan:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

Outcome of uname -mr:
2.6.27-11-generic i686

Hopefully this helps.....

---

### Post by mwhite1206 on 2009-03-09
The following solved the sound issue:
[http://ossarchives.blogspot.com/2008/10/troubleshooting-your-sound.html](http://ossarchives.blogspot.com/2008/10/troubleshooting-your-sound.html)

Still no progress on the wireless issue.

---

### Post by mwhite1206 on 2009-03-16
The problem has been solved, see this thread:
[http://ubuntuforums.org/showthread.php?t=1078010](http://ubuntuforums.org/showthread.php?t=1078010)

---

