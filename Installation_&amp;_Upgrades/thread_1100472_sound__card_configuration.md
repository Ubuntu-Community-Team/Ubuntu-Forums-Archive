---
title: "sound  card configuration"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by griffink on 2009-03-19
Hi All
I installed my Ubuntu 6.06 few days back and was not able to configure the soundcard .(the volume control icon showed hda intel and Sigmatel STAC9221 A2 as the two devices).
After installing gstreamer plugins the players Totem,Kaffeine seemed to run the songs but no sound appeared(song tracker moved). alsamixer cmd showed the levels as 100 for each. tried for different formats ogg,spx,wav,mp3.........

When i looke up for solution i found this [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
And followed the steps 1 cat /proc/asound/card0/codec#* | grep Codec
                                         2 [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)
                                         3 options snd-hda-intel model=MODEL
                                                    reboot

results 1 Codec: Sigmatel STAC9221 A2
                               2 searched my card in the Alsa txt and found this
                    STAC9220/9221
990 ref Reference board
991 3stack D945 3stack
992 5stack D945 5stack + SPDIF
993 intel-mac-v1 Intel Mac Type 1
994 intel-mac-v2 Intel Mac Type 2
995 intel-mac-v3 Intel Mac Type 3
996 intel-mac-v4 Intel Mac Type 4
997 intel-mac-v5 Intel Mac Type 5
998 macmini Intel Mac Mini (equivalent with type 3)
999 macbook Intel Mac Book (eq. type 5)
1000 macbook-pro-v1 Intel Mac Book Pro 1st generation (eq. type 3)
1001 macbook-pro Intel Mac Book Pro 2nd generation (eq. type 3)
1002 imac-intel Intel iMac (eq. type 2)
1003 imac-intel-20 Intel iMac (newer version) (eq. type 3)
1004 dell-d81 Dell (unknown)
1005 dell-d82 Dell (unknown)
1006 dell-m81 Dell (unknown)
1007 dell-m82 Dell XPS M121

                          3 As my Motherboard is Intel 945 I replaced MODEL with 3stack as asked in the
                                              help.ubuntu.com site

Now after reboot,---------------the volume control icon got red (blocked) and error appears as "No volume control gstreamer plugin/device found."
                            ---------------the aplay cmd shows
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:544: audio open error: No such device
                       ---------------------the cat /proc/asound/card0/codec#* | grep Codec shows no such directory.
                     ---------------Totem on playing starts with error as could not establish connxn with sound server.

The result of $ lspci -v
0000:00:00.0 Host bridge: Intel Corporation 945G/P Memory Controller Hub (rev 02)
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:02.0 VGA compatible controller: Intel Corporation 945G Integrated Graphics Controller (rev 02) (prog-if 00 [VGA])
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at fea80000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at dc00 [size=8]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at fea40000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <available only to root>

0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at fea38000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at d880 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at d800 [size=32]

0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at d480 [size=32]

0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, medium devsel, latency 0, IRQ 193
        I/O ports at d400 [size=32]

0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, medium devsel, latency 0, IRQ 185
        Memory at fea37c00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: feb00000-febfffff
        Capabilities: <available only to root>

0000:00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, medium devsel, latency 0
        Capabilities: <available only to root>

0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at ffa0 [size=16]

0000:00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 177
        I/O ports at d080 [size=8]
        I/O ports at d000 [size=4]
        I/O ports at cc00 [size=8]
        I/O ports at c880 [size=4]
        I/O ports at c800 [size=16]
        Capabilities: <available only to root>

0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: medium devsel, IRQ 10
        I/O ports at 0400 [size=32]

0000:01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Elitegroup Computer Systems: Unknown device 8139
        Flags: bus master, medium devsel, latency 64, IRQ 201
        I/O ports at e800 [size=256]
        Memory at febffc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

templar@templar-desktop:~$ lspci -v
0000:00:00.0 Host bridge: Intel Corporation 945G/P Memory Controller Hub (rev 02)
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:02.0 VGA compatible controller: Intel Corporation 945G Integrated Graphics Controller (rev 02) (prog-if 00 [VGA])
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at fea80000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at dc00 [size=8]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at fea40000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <available only to root>

0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at fea38000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at d880 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at d800 [size=32]

0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at d480 [size=32]

0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, medium devsel, latency 0, IRQ 193
        I/O ports at d400 [size=32]

0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, medium devsel, latency 0, IRQ 185
        Memory at fea37c00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: feb00000-febfffff
        Capabilities: <available only to root>

0000:00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, medium devsel, latency 0
        Capabilities: <available only to root>

0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at ffa0 [size=16]

0000:00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 177
        I/O ports at d080 [size=8]
        I/O ports at d000 [size=4]
        I/O ports at cc00 [size=8]
        I/O ports at c880 [size=4]
        I/O ports at c800 [size=16]
        Capabilities: <available only to root>

0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
        Subsystem: Elitegroup Computer Systems: Unknown device 2633
        Flags: medium devsel, IRQ 10
        I/O ports at 0400 [size=32]

0000:01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Elitegroup Computer Systems: Unknown device 8139
        Flags: bus master, medium devsel, latency 64, IRQ 201
        I/O ports at e800 [size=256]
        Memory at febffc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

------------------------RESULT of sudo lsmod
Module Size Used by
snd_opl3_lib 10624 0
snd_hwdep 9376 1 snd_opl3_lib
snd_sb16_dsp 11520 0
snd_sb_common 15616 1 snd_sb16_dsp
snd_mpu401_uart 7808 0
snd_rawmidi 25504 1 snd_mpu401_uart
snd_seq_device 8716 2 snd_opl3_lib,snd_rawmidi
rfcomm 40216 0
l2cap 26372 5 rfcomm
bluetooth 50020 4 rfcomm,l2cap
ipt_limit 2432 0
ip_nat_irc 2688 0
ip_nat_ftp 3328 0
iptable_nat 7812 0
iptable_mangle 2944 0
ipt_LOG 6912 0
ipt_MASQUERADE 3456 0
ip_nat 19628 4 ip_nat_irc,ip_nat_ftp,iptable_nat,ipt_MASQUERADEipt_TOS 2560 0
ipt_REJECT 5632 0
ip_conntrack_irc 6768 1 ip_nat_irc
ip_conntrack_ftp 7792 1 ip_nat_ftp
ipt_state 2048 0
ip_conntrack 51500 8 ip_nat_irc,ip_nat_ftp,iptable_nat,ipt_MASQUERADE,ip_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
nfnetlink 6552 2 ip_nat,ip_conntrack
ppdev 9220 0
speedstep_lib 4484 0
cpufreq_userspace 4696 0
cpufreq_stats 5636 0
freq_table 4740 1 cpufreq_stats
cpufreq_powersave 1920 0
cpufreq_ondemand 6428 0
cpufreq_conservative 7332 0
video 16260 0
tc1100_wmi 6916 0
sony_acpi 5644 0
pcc_acpi 12416 0
hotkey 11556 0
dev_acpi 11140 0
container 4608 0
button 6672 0
acpi_sbs 19980 0
battery 9988 1 acpi_sbs
ac 5252 1 acpi_sbs
i2c_acpi_ec 5120 1 acpi_sbs
i2c_core 21904 1 i2c_acpi_ec
ipt_TCPMSS 4608 0
ipt_tcpmss 2432 0
iptable_filter 3072 0
ip_tables 22400 11 ipt_limit,iptable_nat,iptable_mangle,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,ipt_state,ipt_TCPMSS,ipt_tcpmss,iptable_filter
pppoe 14400 2
pppox 3720 1 pppoe
ipv6 266112 8
ppp_generic 30100 6 pppoe,pppox
slhc 7424 1 ppp_generic
af_packet 22920 2
nls_utf8 2176 1
ntfs 103536 1
nls_iso8859_1 4224 4
nls_cp437 5888 4
vfat 13440 4
fat 53020 1 vfat
dm_mod 59192 1
md_mod 72532 0
lp 11844 0
tsdev 8000 0
8139cp 22528 0
8139too 26880 0
mii 5888 2 8139cp,8139too
parport_pc 35780 1
parport 36296 3 ppdev,lp,parport_pc
pcspkr 2180 0
psmouse 36100 0
serio_raw 7300 0
rtc 13492 0
intel_agp 22940 1
agpgart 34888 1 intel_agp
snd_hda_codec 157616 0
snd_pcm_oss 53664 0
snd_mixer_oss 18688 1 snd_pcm_oss
snd_pcm 89864 3 snd_sb16_dsp,snd_hda_codec,snd_pcm_oss
snd_timer 25220 2 snd_opl3_lib,snd_pcm
snd 55268 12 snd_opl3_lib,snd_hwdep,snd_sb16_dsp,snd_sb_common,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore 10208 1 snd
snd_page_alloc 11272 1 snd_pcm
sg 37920 0
evdev 9856 1
ext3 135944 1
jbd 58772 1 ext3
ide_generic 1536 0
ehci_hcd 34184 0
uhci_hcd 33808 0
usbcore 130820 3 ehci_hcd,uhci_hcd
sd_mod 19984 8
ata_piix 11012 14
libata 78992 1 ata_piix
scsi_mod 139496 3 sg,sd_mod,libata
ide_cd 33028 0
cdrom 38560 1 ide_cd
piix 11012 1
generic 5124 0
thermal 13576 0
processor 23360 1 thermal
fan 4868 0
capability 5000 0
commoncap 7296 1 capability
vga16fb 13704 1
vgastate 10368 1 vga16fb
fbcon 42784 72
tileblit 2816 1 fbcon
font 8320 1 fbcon
bitblit 6272 1 fbcon
softcursor 2304 1 bitblit

  Please reply with a solution...........

---

### Post by bertolo on 2009-04-06
> I installed my Ubuntu 6.06 few days back and was not able to configure the soundcard
upgrade to 8.10 plz

---

