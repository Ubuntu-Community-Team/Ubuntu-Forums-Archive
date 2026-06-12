---
title: "DVD drive not recognized once installed"
date: 2009-03-30
forum: Hardware
---

### Post by Julolidine on 2009-03-30
So I can boot a live-CD to get into Ubuntu - validating that the drive works.  However, recently the drive has become not accessible in Ubuntu.  

sudo lshw -C disk 
```
  *-disk                  
       description: ATA Disk
       product: ST9250421AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: HP14
       serial: 5TH0AWP9
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0007ef35

```

Which does not show my CD-Rom

cat /etc/fstab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9ddc5919-94fe-4ee8-9dd3-91ec763e1afc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=b9eb3d2d-63af-4510-99f4-429342d1b3d3 /home           ext3    relatime        0       2
# /dev/sda7
UUID=4A92-E7BF  /shared         vfat    utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=DD52-2AAC  /windows        vfat    utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=08bd4c6f-b96c-4b82-99d0-bdf715531856 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```


lsmod

```
Module                  Size  Used by
ipv6                  263972  14 
af_packet              25728  4 
binfmt_misc            16904  1 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
vboxnetflt             92168  0 
vboxdrv               118824  1 vboxnetflt
ppdev                  15620  0 
acpi_cpufreq           15500  1 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
cpufreq_ondemand       14988  1 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       9856  0 
cpufreq_conservative    14600  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
pci_slot               12680  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
nls_iso8859_1          12032  2 
nls_cp437              13696  2 
vfat                   18816  2 
fat                    57376  1 vfat
ata_piix               24580  0 
sbp2                   29324  0 
lp                     17156  0 
pata_pcmcia            18944  1 
joydev                 18368  0 
pcmcia                 43052  1 pata_pcmcia
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
iwlagn                 99716  0 
iwlcore                94532  1 iwlagn
rfkill                 17176  2 iwlcore
serio_raw              13444  0 
led_class              12164  1 iwlcore
evdev                  17696  10 
psmouse                45200  0 
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
pcspkr                 10624  0 
yenta_socket           31756  3 
rsrc_nonstatic         19072  1 yenta_socket
pcmcia_core            43412  4 pata_pcmcia,pcmcia,yenta_socket,rsrc_nonstatic
mac80211              216820  2 iwlagn,iwlcore
ricoh_mmc              11904  0 
sdhci_pci              15360  0 
sdhci                  23940  1 sdhci_pci
mmc_core               58268  1 sdhci
cfg80211               32392  3 iwlagn,iwlcore,mac80211
snd_hda_intel         384176  3 
container              11520  0 
tpm_infineon           17064  0 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
tpm                    22848  1 tpm_infineon
tpm_bios               14080  1 tpm
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
video                  25232  0 
output                 11008  1 video
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
wmi                    14504  0 
intel_agp              33724  0 
ac                     12292  0 
battery                18436  0 
button                 14224  0 
agpgart                42184  1 intel_agp
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133256  2 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sd_mod                 42392  6 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ohci1394               37936  0 
ahci                   37132  5 
ieee1394               96324  2 sbp2,ohci1394
libata                178208  3 ata_piix,pata_pcmcia,ahci
scsi_mod              155212  4 sbp2,sd_mod,sg,libata
dock                   16656  1 libata
ehci_hcd               43788  0 
uhci_hcd               30736  0 
usbcore               149360  3 ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

```

which doesn't show modules such as cd-rom, sr_mod.  Trying to insert those modules either manually or into /etc/modules results in no resolution.  

This is a HP Elitebook 6930p

This is a difficult problem to search for, as there are too many off target hits.  

Any help is appreciated.

---

### Post by Concussion on 2009-03-30
Sorry to piggyback on this thread but it is the same thing that I am dealing with.
I have looked at every post under the sun to find the answer. 

Linux 64studio 2.6.21-1-multimedia-amd64 #1 SMP PREEMPT RT Fri Jun 22 00:00:33 UTC 2007 x86_64 GNU/Linux



```
mount: special device /dev/scd0 does not exist

```

fstab

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

lsmod

```
Module                  Size  Used by
isofs                  40316  0
udf                    82568  0
rfcomm                 50216  0
l2cap                  33280  5 rfcomm
bluetooth              66692  4 rfcomm,l2cap
ipv6                  303744  12
capability             10504  0
commoncap              12672  1 capability
ppdev                  14088  0
parport_pc             42536  0
lp                     18824  0
parport                45836  3 ppdev,parport_pc,lp
button                 13984  0
ac                     10888  0
battery                16136  0
dm_snapshot            21880  0
dm_mirror              27072  0
dm_mod                 67472  2 dm_snapshot,dm_mirror
prism54                61832  0
snd_seq_dummy           8836  0
snd_seq_oss            39168  0
snd_seq_midi           13888  0
snd_rawmidi            31520  1 snd_seq_midi
snd_seq_midi_event     12928  2 snd_seq_oss,snd_seq_midi
snd_seq                61056  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device         13460  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sbp2                   29316  0
irtty_sir              13824  0
sir_dev                22152  1 irtty_sir
joydev                 15616  0
tsdev                  13312  0
8250_pnp               16768  0
pcmcia                 45520  0
snd_hda_intel         435672  1
snd_pcm_oss            48288  0
snd_mixer_oss          22528  1 snd_pcm_oss
snd_pcm                89096  2 snd_hda_intel,snd_pcm_oss
tifm_7xx1              14720  0
snd_timer              30088  2 snd_seq,snd_pcm
sdhci                  23820  0
i2c_i801               14748  0
irda                  202092  2 irtty_sir,sir_dev
yenta_socket           32396  1
snd_page_alloc         16144  2 snd_hda_intel,snd_pcm
8250                  115784  1 8250_pnp
tifm_core              16128  1 tifm_7xx1
mmc_core               35336  1 sdhci
ipw3945               200096  0
crc_ccitt               6912  1 irda
rsrc_nonstatic         16640  1 yenta_socket
snd_hwdep              15496  1 snd_hda_intel
i2c_core               29952  1 i2c_i801
serial_core            27520  1 8250
psmouse                45072  0
pcmcia_core            47956  3 pcmcia,yenta_socket,rsrc_nonstatic
snd                    72776  13 snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep
serio_raw              12420  0
iTCO_wdt               16768  0
soundcore              14112  1 snd
ieee80211              38984  1 ipw3945
ieee80211_crypt        11392  1 ieee80211
firmware_class         16128  3 prism54,pcmcia,ipw3945
pcspkr                  8320  0
intel_agp              31808  1
evdev                  15616  4
ext3                  138000  1
jbd                    67824  1 ext3
mbcache                14600  1 ext3
sd_mod                 27136  3
ata_generic            14340  0
ata_piix               20740  2
libata                126496  2 ata_generic,ata_piix
scsi_mod              163768  3 sbp2,sd_mod,libata
ohci1394               40136  0
r8169                  37384  0
ieee1394              110776  2 sbp2,ohci1394
generic                10884  0 [permanent]
ehci_hcd               38540  0
ide_core              162304  1 generic
uhci_hcd               30368  0
thermal                20880  0
processor              40552  1 thermal
fan                    10504  0
vga16fb                17432  0
vgastate               12800  1 vga16fb

```

and for some reason this command doesn't do anything for me

```
brian@64studio:~$ sudo lshw -C disk
sudo: lshw: command not found

```

---

### Post by Julolidine on 2009-03-30
I figured mine out somehow.  I had tweaked around with the BIOS, and nothing that I did should have affected the DVD player (ie shutting off bluetooth), but somehow it did.  Restored BIOS to original manufacturers, and it was fine.

---

### Post by Concussion on 2009-03-30
Intersting. Well I'm glad to hear that you were able to fix the issue. 
Since posting I have found several posts pertaining the the same laptop model that I am using, and it seems to be an issue with the bios and using grub. 

The issue is solved by using lilo instead of grub. I'm currently having trouble getting lilo to be my boot loader. I've run all of the instructions listed for switching from grub to lilo, but I keep ending up with the grub loader. 

My system is a 
Clevo m570U

So that is where I stand at the moment. 

The issue with grub makes it so that my dvd is not listed in WinXp either.

---

### Post by Concussion on 2009-03-30
Minutes after the previous post I found a fix in another thread with the same model laptop. 

All that I had to do was enable the RAID option in the bois. 

Even though I only have one HD and one DVD drive it worked. 

I still have an icon for the CD-ROM that doesn't mount, but I now have another icon that says DVD-ROM and it does mount. 

I can live with the extra icon.

---

