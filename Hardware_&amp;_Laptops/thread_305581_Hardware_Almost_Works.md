---
title: "Hardware Almost Works"
date: 2006-11-23
forum: Hardware &amp; Laptops
---

### Post by redDEADresolve on 2006-11-23
I am having a problem with my internal card reader in my desktop. It's a  LINKSKEY LKA-CR15B 19-in-1 USB 2.0 Card Reader/Writer. In Dapper it worked no problem. When I upgraded to Edgy it doesn't read cards, although the light goes on. I'm confused to whats happened. The USB slot works, it reads and writes data but the card slots don't. I've tried a couple of cards and have no idea what to do. 

I did get this by typing "lspci"> 
red@red-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub (rev 81)
00:01.0 PCI bridge: Intel Corporation 945G/GZ/P/PL Express PCI Express Root Port (rev 81)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]
01:00.1 Display controller: ATI Technologies Inc RV530 [Radeon X1600] (Secondary)
02:03.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)


---

### Post by redDEADresolve on 2006-11-24
I also got this when I typed lsmod
> 
red@red-desktop:~$ lsmod - Edgy Output
Module                  Size  Used by
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
fglrx                 415180  50 
speedstep_lib           5764  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sony_acpi               6412  0 
sbs                    16804  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
container               5632  0 
button                  7952  0 
battery                11652  0 
asus_acpi              17688  0 
ac                      6788  0 
ipv6                  272288  12 
af_packet              24584  2 
nls_utf8                3200  1 
ntfs                  112116  1 
w83627hf               28560  0 
hwmon_vid               4096  1 w83627hf
eeprom                  8208  0 
i2c_isa                 6144  1 w83627hf
i2c_i801                9868  0 
i2c_core               23424  5 i2c_ec,w83627hf,eeprom,i2c_isa,i2c_i801
lp                     12964  0 
r1000                  17792  0 
rt2500                188004  1 
sg                     37404  0 
r8169                  32136  0 
tsdev                   9152  0 
snd_hda_intel          20116  5 
snd_hda_codec         164608  1 snd_hda_intel
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25348  2 snd_pcm
intel_agp              26012  1 
agpgart                34888  2 fglrx,intel_agp
usbhid                 45152  0 
snd                    58372  14 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
floppy                 63044  0 
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
psmouse                41352  0 
serio_raw               8452  0 
evdev                  11392  2 
pcspkr                  4352  0 
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
ext3                  142728  1 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  4 usbhid,ehci_hcd,uhci_hcd
ide_generic             2432  0 
sr_mod                 18212  0 
cdrom                  38944  1 sr_mod
sd_mod                 22656  4 
generic                 5764  0 
ata_piix               11780  3 
libata                 74892  1 ata_piix
scsi_mod              144648  4 sg,sr_mod,sd_mod,libata
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

---

### Post by WirelessMike on 2007-02-16
If you ever get a fix for this, please pm me immediately!

The only fix I know of at this time without installing an alternative distro (such as Debian, which my friend confirmed works on that very hardware) is to discover which kernel "update" screwed up detection and "downgrade" to the better kernel.

---

### Post by WirelessMike on 2007-03-07
The most recent kernel upgrade in Edgy got this working again for me.

---

