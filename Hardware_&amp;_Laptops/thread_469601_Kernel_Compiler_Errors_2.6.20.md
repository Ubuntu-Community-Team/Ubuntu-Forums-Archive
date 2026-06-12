---
title: "Kernel Compiler Errors 2.6.20"
date: 2007-06-10
forum: Hardware &amp; Laptops
---

### Post by beardiggin on 2007-06-10
Can anyone help me debug this problem.  Here is the error output from my compiler:

  Building modules, stage 2.
  MODPOST 520 modules
WARNING: "cx2341x_mpeg_ctrls" [ubuntu/media/ivtv/ivtv.ko] undefined!
WARNING: "cx2341x_fill_defaults" [ubuntu/media/ivtv/ivtv.ko] undefined!
WARNING: "cx2341x_log_status" [ubuntu/media/ivtv/ivtv.ko] undefined!
WARNING: "cx2341x_ctrl_get_menu" [ubuntu/media/ivtv/ivtv.ko] undefined!
WARNING: "cx2341x_update" [ubuntu/media/ivtv/ivtv.ko] undefined!
WARNING: "cx2341x_ctrl_query" [ubuntu/media/ivtv/ivtv.ko] undefined!
WARNING: "cx2341x_ext_ctrls" [ubuntu/media/ivtv/ivtv.ko] undefined!
make[2]: *** [__modpost] Error 1
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.20'
make: *** [debian/stamp-build-kernel] Error 2


I am compiling this kernel on a Toshiba Tecra M7

The following output may or may not be useful:
---------------------------------------------------------------------------------------------------------------------------
lspci output

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
01:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
03:0b.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:0b.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
03:0b.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
03:0b.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

---------------------------------------------------------------------------------------------------------------------------
lsmod output

Module                  Size  Used by
arc4                    2944  2 
ecb                     4480  2 
blkcipher               6784  1 ecb
ieee80211_crypt_wep     6144  1 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ipv6                  268960  14 
ppdev                  10116  0 
i915                   24448  2 
drm                    81044  3 i915
acpi_cpufreq           10056  0 
cpufreq_conservative     8200  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
cpufreq_ondemand        9228  2 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
pcc_acpi               13184  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
dev_acpi               12292  0 
sbs                    15652  0 
video                  16388  0 
button                  8720  0 
asus_acpi              17308  0 
container               5248  0 
ac                      6020  0 
i2c_ec                  6016  1 sbs
i2c_core               22656  1 i2c_ec
battery                10756  0 
toshiba_acpi           11972  0 
backlight               7040  2 asus_acpi,toshiba_acpi
dock                   10268  0 
nls_utf8                3072  1 
ntfs                  107764  1 
sbp2                   23812  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0 
snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
joydev                 10816  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
ipw3945               118816  1 
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ieee80211              34760  1 ipw3945
ieee80211_crypt         7040  2 ieee80211_crypt_wep,ieee80211
iTCO_wdt               11812  0 
pcmcia                 39212  0 
tifm_7xx1               8704  0 
tifm_core              11140  1 tifm_7xx1
iTCO_vendor_support     4868  1 iTCO_wdt
af_packet              23816  8 
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
serio_raw               7940  0 
sdhci                  18700  0 
mmc_core               26756  1 sdhci
tpm_infineon            9112  0 
tpm                    16672  1 tpm_infineon
tpm_bios                8448  1 tpm
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
psmouse                38920  0 
pcspkr                  4224  0 
intel_agp              25244  1 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
agpgart                35400  3 drm,intel_agp
tsdev                   8768  0 
evdev                  11008  5 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  4 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
generic                 5124  0 [permanent]
ata_piix               15492  3 
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
e1000                 126016  0 
ata_generic             9092  0 
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  5 sbp2,sg,sd_mod,sr_mod,libata
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  3 ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

------------------------------------------------------------------------------------------------------------------------------------
cat /proc/cpuinfo 

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2500  @ 2.00GHz
stepping        : 8
cpu MHz         : 1000.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pni monitor vmx est tm2 xtpr
bogomips        : 3994.44
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2500  @ 2.00GHz
stepping        : 8
cpu MHz         : 1000.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pni monitor vmx est tm2 xtpr
bogomips        : 3990.11
clflush size    : 64

---

### Post by neptho on 2007-06-10
Go back through your kernel drivers (make menuconfig), and make sure that you've enabled the "Conexant CX2341x MPEG" entry; then make-kpkg clean; rebuild.

---

### Post by beardiggin on 2007-06-10
Thanks for the input.  I don't think that I have an ivtv card in my system.  I have a Toshiba tecra M7  Tablet PC, and I will be using a usb logitech quickcam messneger for a webcam.  Do I need the ivtv  driver?

Thanks,
Barry

---

