---
title: "Frequency scaling issue"
date: 2007-04-18
forum: Hardware &amp; Laptops
---

### Post by rabidphage on 2007-04-18
Hi

I have a pentium m 740 which refuses to scale properly. It should scale to 600 Mhz but this is as low as it goes.

> cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.73GHz
stepping        : 8
cpu MHz         : 798.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up est tm2
bogomips        : 1597.29
clflush size    : 64

> 
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq
798000

The available frequencies are

> 
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies 
798000 1064000 1330000 1729000 
The upper values are ok but the lowest should be in the whereabouts of 600000 hz if i'm correct.. **Cpu-z under windows reports it as 600 Mhz**

The scaling governor is 
> cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 
ondemand

> uname -a
Linux symbio 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux



Extra info

> lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Radeon Mobility M300]
06:01.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:08.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 02)




> lsmod
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
radeon                124576  2 
drm                    81044  3 radeon
speedstep_centrino      9920  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  1 
cpufreq_conservative     8200  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
freq_table              5792  3 speedstep_centrino,cpufreq_ondemand,cpufreq_stats
tc1100_wmi              8068  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
pcc_acpi               13184  0 
container               5248  0 
button                  8720  0 
sbs                    15652  0 
ac                      6020  0 
video                  16388  0 
battery                10756  0 
i2c_ec                  5888  1 sbs
i2c_core               22784  1 i2c_ec
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
dock                   10268  0 
nls_iso8859_1           5120  2 
nls_cp437               6784  2 
ipv6                  268704  8 
vfat                   14208  2 
fat                    53916  1 vfat
af_packet              23816  2 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
joydev                 10816  0 
snd_intel8x0           34204  1 
snd_ac97_codec         98336  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          17408  1 snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39212  0 
ipw2200               148040  0 
psmouse                38920  0 
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
ieee80211              34760  1 ipw2200
ieee80211_crypt         7040  1 ieee80211
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
intel_agp              25116  1 
serio_raw               7940  0 
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
agpgart                35400  2 drm,intel_agp
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
tsdev                   8768  0 
evdev                  11008  5 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  5 
generic                 5124  0 [permanent]
ata_piix               15492  4 
b44                    28044  0 
mii                     6528  1 b44
ata_generic             9092  0 
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  4 sg,sr_mod,sd_mod,libata
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  3 ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

The battery life suffers, the cpu fan is louder and runs most of the time and apparantly is either on or off

This is a fresh install, Nothing is altered except gnome games has been removed.

I've also had this issue with centos

I have a suspicion that the freq_table is at fault. 

Please help

Thanks in advance..:D

---

### Post by hardyn on 2007-04-18
I have never really stop to think about it, or thought that it has a been a problem, but 798MHz is as low as mine has ever gone; so either both of us are working correctly... or incorrectly?

---

### Post by rabidphage on 2007-04-18
incorrectly I guess 
):P

---

### Post by hardyn on 2007-04-18
it looks as though cpu-z is incorrect.

[http://www.thinkwiki.org/wiki/Intel_Pentium_M_%28Dothan%29](http://www.thinkwiki.org/wiki/Intel_Pentium_M_%28Dothan%29)

both my 770 and your 740 have minimum speeds of 800Mhz

hope this helps.

---

### Post by rabidphage on 2007-04-18
Thanks..

Least expected.. but great find.. :o

---

### Post by rabidphage on 2007-04-18
Now that is solved, can someone help me with the fan issue?

---

### Post by hardyn on 2007-04-18
Yup... you have an Asus or Vaio notebook?

Try the 386 kernel... there is a problem with some PMs and the generic kernel.  Try the 386 kernel, you will get all your performance back, and slow that fan up... i have to do that with my Asus notebook... This should almost be a stickey.

you will also need the 386 retricted libs and the 386 headers.

---

### Post by rabidphage on 2007-04-19
under feisty theres just one generic kernel for x86

---

