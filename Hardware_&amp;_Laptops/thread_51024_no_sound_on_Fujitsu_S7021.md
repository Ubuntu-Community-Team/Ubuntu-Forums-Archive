---
title: "no sound on Fujitsu S7021"
date: 2005-07-22
forum: Hardware &amp; Laptops
---

### Post by wizer on 2005-07-22
Hi
I'm new to Linux. Thot I'd see if I can migrate out of Windows using my new laptop.  But I have been facing a few problems.  One of my problems is I have no sound.

Looking at some of the other posts, I did a lsmod. (I dont see any snd entries)
The results are:
--------- lsmod scan ----------------
Module                  Size  Used by
udf                    77060  1 
ipv6                  229504  6 
speedstep_centrino      7892  1 
proc_intf               4100  0 
freq_table              4100  1 speedstep_centrino
cpufreq_userspace       4572  1 
cpufreq_ondemand        6172  0 
cpufreq_powersave       1920  0 
pcmcia                 21380  2 
video                  16260  0 
sony_acpi               6280  0 
pcc_acpi               11264  0 
button                  6800  0 
battery                10244  0 
container               4608  0 
ac                      4996  0 
af_packet              20744  6 
ohci1394               31876  0 
ipw2200                66156  0 
firmware_class          9728  1 ipw2200
ieee80211              21252  1 ipw2200
ieee80211_crypt         5832  1 ieee80211
yenta_socket           19584  0 
pcmcia_core            53568  2 pcmcia,yenta_socket
tg3                    75524  0 
i2c_i801                8076  0 
i2c_core               21264  1 i2c_i801
piix                    9988  1 
ehci_hcd               29444  0 
uhci_hcd               30224  0 
usbcore               107384  3 ehci_hcd,uhci_hcd
shpchp                 86116  0 
pci_hotplug            30512  1 shpchp
intel_agp              20636  1 
agpgart                31784  1 intel_agp
pcspkr                  3816  0 
rtc                    12216  0 
nls_utf8                2176  1 
ntfs                   97136  1 
nls_iso8859_1           4224  1 
nls_cp437               5888  1 
vfat                   12928  1 
fat                    37792  1 vfat
md                     43856  0 
dm_mod                 53116  1 
capability              5000  0 
commoncap               7808  1 capability
sbp2                   22408  0 
ieee1394              100408  2 ohci1394,sbp2
joydev                  9408  0 
tsdev                   7488  0 
evdev                   9088  1 
psmouse                19336  0 
mousedev               11160  1 
parport_pc             34372  0 
lp                     10792  0 
parport                33480  2 parport_pc,lp
ide_generic             1664  0 
ide_disk               18176  0 
ide_cd                 38532  1 
ide_core              118988  4 piix,ide_generic,ide_disk,ide_cd
ext3                  120968  1 
jbd                    54168  1 ext3
ahci                   10500  0 
sr_mod                 16036  0 
cdrom                  36508  2 ide_cd,sr_mod
sd_mod                 16784  5 
ata_piix                8836  8 
libata                 44548  2 ahci,ata_piix
scsi_mod              119936  5 sbp2,ahci,sr_mod,sd_mod,libata
unix                   26164  569 
thermal                13576  0 
processor              22708  2 speedstep_centrino,thermal
fan                     4612  0 
fbcon                  34048  0 
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0 
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb
-------------------------------------

In Windows XP, my sound driver is listed as Agere High Definition Audio, so I guess the sound chipset from lpsci is 
0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)


Full results of lpsci is
--------- lspci scan ----------------
 PCI_bus
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1c.1 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d4)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
0000:00:1f.2 IDE interface: Intel Corp. 82801FBM (ICH6M) SATA Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
0000:02:00.0 Ethernet controller: Broadcom Corporation: Unknown device 167d (rev 11)
0000:06:03.0 CardBus bridge: O2 Micro, Inc.: Unknown device 7134 (rev 20)
0000:06:03.2 0805: O2 Micro, Inc.: Unknown device 7120
0000:06:03.3 Bridge: O2 Micro, Inc.: Unknown device 7130
0000:06:05.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
0000:06:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
-------------------------------------

Does anyone know how I can get sound.  By the way, I can play a DVD on Totem but there is no sound output.

Thanks
Andrew

---

### Post by wizer on 2005-07-25
:) 
I have found the solution. found it in a post about a Dell 8100 laptop
If you, like me, have a (ICH6 Family) High Definition Audio Controller, you'll need to upgrade your kernel to 2.6.12 to get sound.

For those who cant wait for Breezy to get sound, there a good HowTo on installing a new kernel.
[http://ubuntuforums.org/showthread.php?t=43065&highlight=howto+kernel](http://ubuntuforums.org/showthread.php?t=43065&highlight=howto+kernel)

---

