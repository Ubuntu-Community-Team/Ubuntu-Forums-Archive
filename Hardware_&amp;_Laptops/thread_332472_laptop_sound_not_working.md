---
title: "laptop sound not working"
date: 2007-01-06
forum: Hardware &amp; Laptops
---

### Post by deepsa on 2007-01-06
Hi,

I have lenovo 3000N100 laptop. My sound doesn't work. Here is my lspci -vv

deepsa@deepsa-laptop:~$ lspci -vv
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Lenovo Unknown device 2061
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Lenovo Unknown device 2062
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at b0080000 (32-bit, non-prefetchable) [size=512K]
        Region 1: I/O ports at 1800 [size=8]
        Region 2: Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Region 3: Memory at b0040000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Lenovo Unknown device 2062
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Region 0: Memory at b0100000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Lenovo Unknown device 2066
        Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 21
        Region 0: Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: b0200000-b02fffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Lenovo Unknown device 206b
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 18
        Region 4: I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Lenovo Unknown device 206c
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 19
        Region 4: I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Lenovo Unknown device 206d
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 20
        Region 4: I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Lenovo Unknown device 206e
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin D routed to IRQ 17
        Region 4: I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Lenovo Unknown device 206f
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at b0004000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=05, subordinate=09, sec-latency=32
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: b0300000-b03fffff
        Prefetchable memory behind bridge: 0000000030000000-0000000031ffffff
        Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Lenovo Unknown device 2071
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02) (prog-if 80 [Master])
        Subsystem: Lenovo Unknown device 2072
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 19
        Region 0: I/O ports at <unassigned>
        Region 1: I/O ports at <unassigned>
        Region 2: I/O ports at <unassigned>
        Region 3: I/O ports at <unassigned>
        Region 4: I/O ports at 18b0 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Lenovo Unknown device 2073
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 10
        Region 4: I/O ports at 18c0 [size=32]

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1010
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at b0200000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

05:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Lenovo Unknown device 2074
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (8000ns min, 16000ns max)
        Interrupt: pin A routed to IRQ 22
        Region 0: I/O ports at 2000 [size=256]
        Region 1: Memory at b0300000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

05:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
        Subsystem: Lenovo Unknown device 2075
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168, Cache Line Size: 128 bytes
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at b0301000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=05, secondary=06, subordinate=09, sec-latency=176
        Memory window 0: 30000000-31fff000 (prefetchable)
        Memory window 1: 32000000-33fff000
        I/O window 0: 00002400-000024ff
        I/O window 1: 00002800-000028ff
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
        16-bit legacy interface ports at 0001

05:06.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (prog-if 10 [OHCI])
        Subsystem: Lenovo Unknown device 2076
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (500ns min, 1000ns max)
        Interrupt: pin A routed to IRQ 21
        Region 0: Memory at b0300800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

05:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
        Subsystem: Lenovo Unknown device 2077
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Interrupt: pin B routed to IRQ 18
        Region 0: Memory at b0300400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

05:06.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
        Subsystem: Lenovo Unknown device 2078
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 7
        Region 0: Memory at b0302000 (32-bit, non-prefetchable) [disabled] [size=256]
        Capabilities: <access denied>

05:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
        Subsystem: Lenovo Unknown device 2079
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 7
        Region 0: Memory at b0302400 (32-bit, non-prefetchable) [disabled] [size=256]
        Capabilities: <access denied>

05:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
        Subsystem: Lenovo Unknown device 207a
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 7
        Region 0: Memory at b0302800 (32-bit, non-prefetchable) [disabled] [size=256]
        Capabilities: <access denied>

deepsa@deepsa-laptop:~$ 


And here is my lsmod 

deepsa@deepsa-laptop:~$ lsmod
Module                  Size  Used by
isofs                  38204  1 
udf                    89604  0 
binfmt_misc            13320  1 
rfcomm                 43544  0 
l2cap                  27136  5 rfcomm
i915                   21632  3 
drm                    82068  4 i915
speedstep_centrino     10628  1 
cpufreq_userspace       5664  0 
cpufreq_stats           7744  0 
cpufreq_powersave       2944  0 
cpufreq_ondemand        9740  0 
freq_table              6176  3 speedstep_centrino,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8968  0 
video                  17540  0 
sbs                    16676  0 
i2c_ec                  6144  1 sbs
i2c_core               23936  1 i2c_ec
container               5504  0 
button                  7824  0 
battery                11396  0 
asus_acpi              17688  0 
ac                      6404  0 
af_packet              24968  0 
nls_iso8859_1           5248  1 
nls_cp437               6912  2 
vfat                   14848  1 
fat                    57244  1 vfat
nls_utf8                3200  2 
ntfs                  110580  2 
sbp2                   25988  0 
parport_pc             37668  0 
lp                     12964  0 
parport                39368  2 parport_pc,lp
fuse                   49428  0 
joydev                 11200  0 
pcmcia                 41004  0 
snd_hda_intel          21912  0 
snd_hda_codec         172288  1 snd_hda_intel
snd_pcm_oss            47232  0 
snd_mixer_oss          18432  1 snd_pcm_oss
tsdev                   9152  0 
snd_pcm                84996  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4996  0 
snd_seq_oss            36352  0 
hci_usb                18972  2 
usbhid                 44768  0 
yenta_socket           28940  1 
bluetooth              59620  7 rfcomm,l2cap,hci_usb
psmouse                41224  0 
snd_seq_midi            9984  0 
snd_rawmidi            26752  1 snd_seq_midi
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
snd_seq                58352  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24964  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               8452  0 
ipw3945               124832  1 
rsrc_nonstatic         15104  1 yenta_socket
snd                    58372  10 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sdhci                  19980  0 
mmc_core               27396  1 sdhci
ieee80211              35528  1 ipw3945
ieee80211_crypt         7424  1 ieee80211
pcspkr                  4352  0 
iTCO_wdt               11684  0 
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
intel_agp              26012  1 
agpgart                34888  3 drm,intel_agp
shpchp                 40480  0 
pci_hotplug            34752  1 shpchp
soundcore               9312  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
evdev                  11520  2 
ipv6                  269600  12 
ext3                  143880  3 
jbd                    63272  1 ext3
mbcache                10244  1 ext3
sg                     37788  0 
sr_mod                 18084  1 
cdrom                  39072  1 sr_mod
sd_mod                 23040  8 
ata_piix               17160  8 
ata_generic             8452  0 
libata                112660  2 ata_piix,ata_generic
8139too                28800  0 
scsi_mod              144908  5 sbp2,sg,sr_mod,sd_mod,libata
ohci1394               37552  0 
ieee1394              303672  2 sbp2,ohci1394
8139cp                 26368  0 
mii                     6912  2 8139too,8139cp
ehci_hcd               35080  0 
generic                 6532  0 [permanent]
uhci_hcd               26248  0 
usbcore               143620  5 hci_usb,usbhid,ehci_hcd,uhci_hcd
thermal                15496  0 
processor              32712  2 speedstep_centrino,thermal
fan                     5892  0 
fbcon                  44448  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3456  1 bitblit
vesafb                  9264  0 
capability              6024  0 
commoncap               8704  1 capability
deepsa@deepsa-laptop:~$ 


I have tried model=laptop-eapd in /etc/modprobe.d/options (#options snd-hda-intel model=laptop-eapd)

It too doesn't work.
If I disable Internal Modem from BIOS then my alsamixer shows the card and i can adjust the volume. I did it and played song in every player I know but no sound came out of the speaker.

If I enable Internal modem and boot I get this in the dmesg:
[   32.272000] HDA Intel: probe of 0000:00:1b.0 failed with error -13

My kernel is 
Linux deepsa-laptop 2.6.19-7-generic #2 SMP Mon Dec 4 16:46:19 UTC 2006 i686 GNU/Linux
My ubuntu is fiesty herd 1.

Please help. How can i make my sound work.

Regards
Deepsa

---

### Post by deepsa on 2007-01-06
Hi,

Ubuntu Rocks!! Fiesty is good. I got my sound working. So what I did was go to the wiki and read howto troubleshoot Sound.
Well summarizing it all this is what I did.
First of all I will like to tell you that there is a excellent guide here: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting). Please read it before doing what is given below. (thanks to ikonia at irc)

Step 1) 
sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant

Step 2)
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc1.tar.bz2)
tar jxvf alsa-driver-1.0.14rc1.tar.bz2
cd alsa-driver-1.0.14rc1/
 sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=hda-intel
sudo make
sudo make install

Step 3)
vi /etc/modprobe.d/options
Here I wrote:
options snd-hda-intel model=laptop-eapd
save and quit.

Step 4) Reboot

Step 5) Enable Internal Modem from within the BIOS

Step 6) Booted Ubuntu Fiesty Linux.

Step 7). LOL !!

Sound's working !! Cheers.

Regards
Deepsa

---

### Post by hey560 on 2007-02-19
I have the lenovo 3000 n100 as well and I had sound working about half of the time.

Recompiling latest alsa and adding that option fixed my problems. Thanks for the great post!

For some reason the internal modem was enabled by default for my n100, I dunno why it would be disabled on yours by default.

---

### Post by dypfryst on 2007-04-11
deepsas little guide worked perfect on my hp dv 2000

---

### Post by LunatikOwl on 2007-05-14
i just installed (today) ubuntu feisty on my lenovo n100 and everything works great except the sound...

as a last resort(i'm still a noob) i tried this tutorial(alsa beta/alpha release?) and it didn't compiled well with make. any ideas will be greatly appreciated. 

i'll provide any output on demand.

---

### Post by tyler22 on 2007-05-14
hahahaha step 7 is great!

---

### Post by chestnuttm on 2007-05-14
I will be installing on a Lenovo 3000N tomorrow evening, I will post the results. 

I can see from the "Live CD" that this a very user friendly Linux release. The leader in its field, in my opinion, but time will tell.

From the instal CD options, there ia an "Install with driver update CD", does anyone know how to aquire such a CD image, or am I missing something?

Best Regards;

Mal :)

---

### Post by beta64 on 2007-06-03
I have just install fesity on my new lenovo 3000 N100, the sound doesn't work. Followed deepsa tutorial but during compliation encountered some errors, can anyone help? My knowledge of linux is at best some unix lessons during my ug days some 20 years ago. thanks.

---

### Post by Allysan on 2007-06-03
I tried following these steps exactly (on a Lenovo R60e running Kubuntu) but now all I have is a Volume Control (muted) icon, and when I click it, it shows an empty Kmix window with no volume sliders or anything.  Any ideas?

UPDATE: This somehow managed to make my sound card disappear when I do "aplay -l" in the terminal.  Ermmm... anyone?

---

### Post by beta64 on 2007-06-03
I followed step-by-step according to the web page  [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) and during recompiling the kernel I get this error message:

/usr/src/modules/alsa-driver/include/adriver.h: In function &#8216;snd_pci_orig_save_state&#8217;:
/usr/src/modules/alsa-driver/include/adriver.h:1099: error: too many arguments to function &#8216;pci_save_state&#8217;
/usr/src/modules/alsa-driver/include/adriver.h: In function &#8216;snd_pci_orig_restore_state&#8217;:
/usr/src/modules/alsa-driver/include/adriver.h:1103: error: too many arguments to function &#8216;pci_restore_state&#8217;
make[3]: *** [/usr/src/modules/alsa-driver/acore/memalloc.o] Error 1
make[2]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[1]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [compile] Error 2 

So I am still stuck with a nice OS but without sound.

Anyone please help!

---

### Post by xrat on 2007-06-21
Deepsa,

> **deepsa said:**
> 
Well summarizing it all this is what I did. ...


Many thanks for the instructions. They worked like a charm on

**Lenovo 3000 N100 Model 0768-FPG (manufacturing date 07/04)**
with Ubuntu 7.04 Feisty (Linux 2.6.20-16-generic)

[INDENT]$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd3400000 irq 21[/INDENT]

[INDENT]$ head -n 1 /proc/asound/card0/codec*
Codec: Realtek ALC681-VD[/INDENT]

And, I, too, added to /etc/modprobe.d/options
[INDENT]options snd-hda-intel model=laptop-eapd[/INDENT]

I tried it with "model=3stack" (as ALSA-Configuration.txt suggests) but that did not work. BTW, the internal model is enabled. I did not try it with it being disabled.

Thanks,
-- xrat

---

### Post by klaasvanschelven on 2007-07-03
Ok, thanks a lot. This page (and a few similar ones) is quite helpful. At least my sound is working now, including correct plugin-to-earphones behavior.

The microphone, however, does not yet work. Both microphones can be heard when Unmuted in the mixer, but neither of them actually reaches the programs they are meant to be used in (Skype, audacity, ...).

I'm running Feisty (updated till 3rd July 2007) on a Lenovo 3000 N100 FPG.
I'd be happy to post more details - just tell me which command's outputs are useful.

Thanks to anyone who can help me with this.

Klaas

---

### Post by klaasvanschelven on 2007-07-03
The following page contains information on the model I'm using, however, as of this writing not yet a solution for the problem:

[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_FPG](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_FPG)

---

### Post by klaasvanschelven on 2007-07-03
Ok, I got microphone to work!

I used intstructions here:
[https://answers.launchpad.net/ubuntu/+question/701](https://answers.launchpad.net/ubuntu/+question/701)

Basically, after doing everything mentioned above, also start alsamixer from prompt, use tab and arrow keys to end up at capture and then hit spacebar to turn capturing on.

---

