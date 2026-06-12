---
title: "No sound please help"
date: 2008-11-16
forum: Hardware
---

### Post by cashmoney on 2008-11-16
I cannot get my sound to work for the life of me.  I upgraded hardy 8.04.1 to kernel 2.6.27.6 and the following results.

```
 lsmod | grep snd

```returns nothing

```
ncash@ncash:~$ alsamixer 

alsamixer: function snd_ctl_open failed for default: No such file or directory

```

```
ncash@ncash:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 135M (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

```
ncash@ncash:~$ lsmod
Module                  Size  Used by
vboxdrv                63768  0 
af_packet              18048  4 
binfmt_misc             9224  1 
rfcomm                 34576  2 
l2cap                  21760  13 rfcomm
ppdev                   8452  0 
ipv6                  245284  14 
acpi_cpufreq            8460  1 
cpufreq_userspace       4356  0 
cpufreq_ondemand        7820  1 
cpufreq_stats           6020  0 
freq_table              5504  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     7432  0 
cpufreq_powersave       2944  0 
sbs                    12168  0 
sbshc                   6272  1 sbs
container               4480  0 
iptable_filter          3712  0 
ip_tables              12048  1 iptable_filter
x_tables               15620  1 ip_tables
aes_i586                8832  2 
sbp2                   21388  0 
parport_pc             32036  0 
lp                      9988  0 
parport                35180  3 ppdev,parport_pc,lp
loop                   15244  0 
pcmcia                 34860  0 
joydev                 10432  0 
hci_usb                14104  2 
nvidia               6901204  38 
yenta_socket           23948  1 
bluetooth              57700  7 rfcomm,l2cap,hci_usb
i2c_core               24340  1 nvidia
intel_agp              26044  0 
rsrc_nonstatic         11776  1 yenta_socket
iTCO_wdt               11428  0 
iTCO_vendor_support     4740  1 iTCO_wdt
psmouse                36880  0 
serio_raw               6276  0 
pcspkr                  3584  0 
pcmcia_core            35476  3 pcmcia,yenta_socket,rsrc_nonstatic
agpgart                33608  2 nvidia,intel_agp
shpchp                 29972  0 
pci_hotplug            28068  1 shpchp
button                  7056  0 
video                  17296  10 
output                  3968  1 video
battery                11140  0 
ac                      5124  0 
dcdbas                  7840  0 
evdev                  10400  8 
ext3                  123272  2 
jbd                    45716  1 ext3
mbcache                 8708  1 ext3
sha256_generic         12672  0 
cbc                     4480  2 
sg                     31796  0 
sr_mod                 15044  0 
cdrom                  35488  1 sr_mod
sd_mod                 29208  3 
ata_generic             5764  0 
pata_acpi               5120  0 
ata_piix               17412  2 
tg3                   120580  0 
ohci1394               29744  0 
libphy                 19712  1 tg3
libata                164128  3 ata_generic,pata_acpi,ata_piix
scsi_mod              143308  5 sbp2,sg,sr_mod,sd_mod,libata
ieee1394               85956  2 sbp2,ohci1394
ehci_hcd               34060  0 
uhci_hcd               22928  0 
usbcore               137712  4 hci_usb,ehci_hcd,uhci_hcd
dock                    9360  1 libata
dm_crypt               13828  1 
dm_mirror              18432  0 
dm_log                 10756  1 dm_mirror
dm_snapshot            18468  0 
dm_mod                 54600  11 dm_crypt,dm_mirror,dm_log,dm_snapshot
thermal                16284  0 
processor              34476  4 acpi_cpufreq,thermal
fan                     5380  0 
thermal_sys            11560  4 video,thermal,processor,fan
fuse                   51996  3 

```

```
ncash@ncash:~$ uname -r
2.6.27.6-nateviv

```

---

### Post by tuxxy on 2008-11-16
Can you hear the test sound files play in sound prefs?

---

### Post by cashmoney on 2008-11-16
> **tuxxy said:**
> Can you hear the test sound files play in sound prefs?

no I get error audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

---

### Post by cashmoney on 2008-11-17
Nevermind I fixed it.

Followed this.  [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)  Compiled and installed also from scratch works great.

Nate

---

