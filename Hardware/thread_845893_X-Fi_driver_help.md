---
title: "X-Fi driver help"
date: 2008-07-01
forum: Hardware
---

### Post by Spartecus on 2008-07-01
ok im sure this is something easy but here is what im getting when i go to install the 1.18 drivers


Installation is in progress. Please wait...
tar: /home/stephen/XFiDrv_Linux_US-1.18.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
cd: 498: can't cd to /opt/Creative/XFiDrv_Linux_US-1.18/drivers
/home/stephen/Desktop/XFiDrv_Linux_US-1.18/installer: 498: ./configure: not found
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
Installation Unsuccessful
stephen@stephen-desktop:~$ 

Thanks if anyone can help

---

### Post by dadec on 2008-07-01
Follow this guide:
[URL="http://ubuntuforums.org/showthread.php?t=571656"]
http://ubuntuforums.org/showthread.php?t=571656[/URL]

I've completed this guide but for some reason I can't blacklist my on board sound and it chooses that as the default even though it recognises the x-fi.  Can anyone help?

edit: ossdetect -v gives:

Detected Creative SB X-Fi (EARLY BETA)
Detected Intel High Definition Audio (P35)
Detected Generic USB audio device (BETA)


ossinfo gives:

Version info: OSS 4.0 (b1016/200806162356) (0x00040003) 
Platform: Linux/i686 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 (DCOMP)

Number of audio devices:	10
Number of audio engines:	14
Number of mixer devices:	2


Device objects
 0: osscore0 OSS core services
 1: hdaudio0 Intel HD Audio interrupts=43541 (50389)
    HD Audio controller Intel HD Audio
    Vendor ID    0x8086293e
    Subvendor ID 0x1043829f
     Codec  0: ALC883 (0x10ec0883/0x1043829f)
 2: sbxfi0 Sound Blaster X-Fi (UAA) interrupts=491 (491)
    PCI device 1102:0005, subdevice 1102:6007
 3: ossusb0 USB audio core services


Mixer devices
 0: High Definition Audio ALC883 (Mixer 0 of device object 1)
 1: Sound Blaster X-Fi (UAA) (Mixer 0 of device object 2)

Audio devices
HD Audio play front               /dev/oss/hdaudio0/pcm0  (device index 0)
HD Audio play rear                /dev/oss/hdaudio0/pcm1  (device index 1)
HD Audio play center/LFE          /dev/oss/hdaudio0/pcm2  (device index 2)
HD Audio play side                /dev/oss/hdaudio0/pcm3  (device index 3)
HD Audio play pcm4                /dev/oss/hdaudio0/pcm4  (device index 4)
HD Audio play spdif-out           /dev/oss/hdaudio0/spdout0  (device index 5)
HD Audio rec mix                  /dev/oss/hdaudio0/pcmin0  (device index 6)
HD Audio rec mix                  /dev/oss/hdaudio0/pcmin1  (device index 7)
Sound Blaster X-Fi (UAA) output   /dev/oss/sbxfi0/pcm0  (device index 8 )
Sound Blaster X-Fi (UAA) input    /dev/oss/sbxfi0/pcmin0  (device index 9)

lsmod gives:
Module                  Size  Used by
af_packet              23812  4 
ipv6                  267780  14 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
[COLOR="Red"]ossusb                 56072  1 
sbxfi                  30320  1 
hdaudio               129960  3 
osscore               564400  3 ossusb,sbxfi,hdaudio[/COLOR]
ppdev                  10372  0 
acpi_cpufreq           10796  3 
cpufreq_stats           7104  0 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
sbs                    15112  0 
container               5632  0 
video                  19856  0 
output                  4736  1 video
dock                   11280  0 
sbshc                   7680  1 sbs
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
aes_i586               33536  0 
dm_crypt               15364  0 
dm_mod                 62660  1 dm_crypt
ac                      6916  0 
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
rt61pci                25472  0 
rt2x00pci              11264  1 rt61pci
atl1                   36364  0 
rt2x00lib              22528  2 rt61pci,rt2x00pci
mii                     6400  1 atl1
nvidia               7825536  34 
evdev                  13056  3 
rfkill                  8592  1 rt2x00lib
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
mac80211              165652  3 rt61pci,rt2x00pci,rt2x00lib
cfg80211               15112  1 mac80211
eeprom_93cx6            3200  1 rt61pci
i2c_core               24832  1 nvidia
button                  9232  0 
shpchp                 34452  0 
intel_agp              25492  0 
agpgart                34760  2 nvidia,intel_agp
pcspkr                  4224  0 
pci_hotplug            30880  1 shpchp
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  1 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
ata_generic             8324  0 
usbhid                 31872  0 
hid                    38784  1 usbhid
ata_piix               19588  2 
ohci1394               33584  0 
pata_acpi               8320  0 
floppy                 59588  0 
pata_jmicron            7040  1 
ieee1394               93752  2 sbp2,ohci1394
ahci                   28420  0 
libata                159344  5 ata_generic,ata_piix,pata_acpi,pata_jmicron,ahci
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  5 ossusb,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 

Thanks in advance

---

