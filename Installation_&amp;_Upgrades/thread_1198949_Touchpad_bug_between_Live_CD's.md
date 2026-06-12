---
title: "Touchpad bug between Live CD's"
date: 2009-06-28
forum: Installation &amp; Upgrades
---

### Post by Done_Fishin on 2009-06-28
Using Live CD's (Ubuntu 8.04 or nUbuntu based on 8.04) the touchpad on the Philips badged Twinhead 12D Stylebook (Philips Freevent X50 / F12DT) functions straight from boot.

Booting though from the Live 9.04 CD or the Super OS 9.04 Live CD ends up with a boot that has no touchpad function, except the left right buttons.

Under Windows, since there is no listing for a touchpad device yet there is a listing for a Microsoft PS/2 Mouse (directly connected to the PS/2 port) where both mouse and port that don't exist, I think that the touchpad is an extension of the serial mouse driver.

I tried adding a PS/2 mouse using a PS/2 to USB adapter both before and during Live CD Boot however 9.04 ignored both instances.


what I am supposed to mount to make it work?

**_8.04 info from terminal _**

> **ubuntu@ubuntu:~$ lsmod**
Module                  Size  Used by
i915                   32512  2 
drm                    82452  3 i915
ipv6                  267780  8 
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
apm                    22616  2 
speedstep_centrino      9152  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 speedstep_centrino,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8712  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
pcmcia                 40876  0 
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
yenta_socket           27276  1 
sdhci                  19076  0 
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ipw2200               146120  0 
rsrc_nonstatic         13696  1 yenta_socket
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ieee80211              35528  1 ipw2200
serio_raw               7940  0 
mmc_core               51460  1 sdhci
evdev                  13056  1 
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
ieee80211_crypt         7040  1 ieee80211
intel_agp              25492  1 
iTCO_wdt               13092  0 
psmouse                40336  0 
pcspkr                  4224  0 
soundcore               8800  1 snd
agpgart                34760  3 drm,intel_agp
iTCO_vendor_support     4868  1 iTCO_wdt
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
squashfs               49160  1 
loop                   18948  2 
unionfs                76752  1 
isofs                  36388  1 
nls_iso8859_1           4992  0 
nls_cp437               6656  1 
vfat                   14464  0 
fat                    54556  1 vfat
sg                     36880  0 
sr_mod                 17956  1 
cdrom                  37408  1 sr_mod
sd_mod                 30720  0 
ata_piix               19588  1 
pata_acpi               8320  0 
8139too                27520  0 
ata_generic             8324  0 
libata                159344  3 ata_piix,pata_acpi,ata_generic
ohci1394               33584  0 
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
ieee1394               93752  1 ohci1394
8139cp                 24704  0 
mii                     6400  2 8139too,8139cp
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  3 ehci_hcd,uhci_hcd
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
i915                   32512  2 
drm                    82452  3 i915
ipv6                  267780  8 
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
apm                    22616  2 
speedstep_centrino      9152  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 speedstep_centrino,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8712  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
pcmcia                 40876  0 
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
yenta_socket           27276  1 
sdhci                  19076  0 
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ipw2200               146120  0 
rsrc_nonstatic         13696  1 yenta_socket
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ieee80211              35528  1 ipw2200
serio_raw               7940  0 
mmc_core               51460  1 sdhci
evdev                  13056  1 
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
ieee80211_crypt         7040  1 ieee80211
intel_agp              25492  1 
iTCO_wdt               13092  0 
psmouse                40336  0 
pcspkr                  4224  0 
soundcore               8800  1 snd
agpgart                34760  3 drm,intel_agp
iTCO_vendor_support     4868  1 iTCO_wdt
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
squashfs               49160  1 
loop                   18948  2 
unionfs                76752  1 
isofs                  36388  1 
nls_iso8859_1           4992  0 
nls_cp437               6656  1 
vfat                   14464  0 
fat                    54556  1 vfat
sg                     36880  0 
sr_mod                 17956  1 
cdrom                  37408  1 sr_mod
sd_mod                 30720  0 
ata_piix               19588  1 
pata_acpi               8320  0 
8139too                27520  0 
ata_generic             8324  0 
libata                159344  3 ata_piix,pata_acpi,ata_generic
ohci1394               33584  0 
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
ieee1394               93752  1 ohci1394
8139cp                 24704  0 
mii                     6400  2 8139too,8139cp
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  3 ehci_hcd,uhci_hcd
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 
ubuntu@ubuntu:~$ 



**ubuntu@ubuntu:~$ lspci**
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
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
01:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
01:05.0 CardBus bridge: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller (rev 21)
01:05.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
01:05.3 Bridge: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
01:05.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
ubuntu@ubuntu:~$ 



**_9.04 info from terminal_**

> **ubuntu@ubuntu:~$ lsmod**
Module                  Size  Used by
binfmt_misc            16776  1 
i915                   65540  2 
drm                    96296  3 i915
ppdev                  15620  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
snd_intel8x0           37532  3 
joydev                 18368  0 
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
pcmcia                 44748  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
ipw2200               150984  0 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               19108  0 
psmouse                61972  0 
yenta_socket           32396  1 
iTCO_vendor_support    11652  1 iTCO_wdt
rsrc_nonstatic         19328  1 yenta_socket
sdhci_pci              15232  0 
serio_raw              13316  0 
snd                    62628  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ieee80211              38344  1 ipw2200
sdhci                  23940  1 sdhci_pci
soundcore              15200  1 snd
ieee80211_crypt        13444  1 ieee80211
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp
squashfs               46344  1 
aufs                  165924  1 
exportfs               12544  1 aufs
isofs                  39844  1 
nls_iso8859_1          12032  0 
nls_cp437              13696  1 
vfat                   18816  0 
fat                    58272  1 vfat
ohci1394               38576  0 
8139too                32128  0 
8139cp                 27776  0 
mii                    13312  2 8139too,8139cp
ieee1394               94660  1 ohci1394
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit




**ubuntu@ubuntu:~$ lspci**
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
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
01:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
01:05.0 CardBus bridge: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller (rev 21)
01:05.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
01:05.3 Bridge: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
01:05.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
ubuntu@ubuntu:~$ 


---

### Post by Done_Fishin on 2009-06-28
Apparently this is a bug as I thought and from the bug report I gleaned this info.


> To get this to work on startup you just need to run the following command:

echo "options psmouse proto=imps" |sudo tee -a /etc/modprobe.d/psmouse

It's not a fix, but it's a good workaround.


> This work around by Sebastian Urban, solves the problem with no obvious side effects:

sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps

The first solution didn't work for me when booting the live Cd perhaps because I didn't know where to place it .. 

The second worked fine from within a terminal window after loading the live CD.

however I am now looking for a way to integrate this into either the CD or an installed version of Ubuntu.

Anyone help me with a few ideas? I know I can create & run a script every time I boot, but what about something a bit more automatic or that doesn't require user intervention.

Thanks

---

### Post by Done_Fishin on 2009-06-29
it seems that there is a Ubuntu Karmic 9.10 version pending .. it's at alpha 2 stage and the problem has been fixed .. an alpha 3 stage is planned and on the way because of various problems including GRUB

---

### Post by Done_Fishin on 2009-07-06
In spite of playing around with the new 9.10 Karmic Alpha2 version which allows the touchpad to work, I also dug into the question of how to make it work in this 9.04 version.

all the information is shown above ..



I created a file using gedit called psmouse which I saved in /etc/modprobe.d/

the contents of the psmouse file are 
> options psmouse proto=imps 

my touchpad loads now at every boot

):P

---

