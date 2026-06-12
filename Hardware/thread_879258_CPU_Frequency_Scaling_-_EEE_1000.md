---
title: "CPU Frequency Scaling - EEE 1000"
date: 2008-08-03
forum: Hardware
---

### Post by Jws0001 on 2008-08-03
Hi guys.  I just picked up an EEE 1000 and so far everything has been going well... except for frequency scaling.  The thing is always maxed out at 1.6ghz no matter what.  I'd really like to cap it at 800mhz - 1.07ghz on battery and dynamic on AC but I can't seem to figure out how. My available frequencies are 1.6ghz, 1.33ghz, 1.07ghz, and 800mhz (Intel Atom proc).

Can someone help me configure this?  I've been searching all over trying to get it to work.

---

### Post by terry f on 2008-08-04
[http://geeksok.com/blog/2008/07/ubuntu-cpu-frequency-selector/]("http://geeksok.com/blog/2008/07/ubuntu-cpu-frequency-selector/")

let me know if it works. I ordered a eee 1000 off amazon, and have not got it yet.  How do you like yours.

---

### Post by maartsen on 2008-08-05
Hi there,

I've installed Ubuntu 8.04 LTS on my server (which is an Intel Atom D945GCLF).

If I try to startup powernowd i get this:
[FONT="Courier New"]
 * Starting powernowd...
 * CPU frequency scaling not supported...                                [ OK ][/FONT]

So I've checked if the modules are loaded, but I cannot load the speedstep centrino modules (or any speedstep module for that fact). It gives a "no such device" error.

The question is now. Has somebody got a working configuration for cpu throttling with the Intel Atom?

---

### Post by terry f on 2008-08-05
I think the article I posted a link to was written for the eee 901 and 1000, and both of them use the atom.

---

### Post by maartsen on 2008-08-06
Hi Terry,

Can you please post a lsmod, so that I can see what modules you have loaded.

The problem I have, that I'm running Ubuntu server edition and I don't have Gnome (or X) installed on that box.

Thanks,
Michel

---

### Post by terry f on 2008-08-06
```
terry@terry-laptop:~$ lsmod
Module                  Size  Used by
af_packet              27272  4 
isofs                  39464  1 
udf                    91048  0 
binfmt_misc            14860  1 
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67748  4 rfcomm,l2cap
b44                    33168  0 
ssb                    39428  1 b44
mii                     7552  1 b44
ndiswrapper           243872  0 
ppdev                  11400  0 
ipv6                  311848  14 
powernow_k8            16608  1 
cpufreq_userspace       6180  0 
cpufreq_conservative    10632  0 
cpufreq_ondemand       11152  1 
cpufreq_stats           8416  0 
freq_table              6464  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       3200  0 
sbs                    17808  0 
sbshc                   8960  1 sbs
container               6656  0 
dock                   12960  0 
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
parport_pc             41128  0 
lp                     14916  0 
parport                44300  3 ppdev,parport_pc,lp
joydev                 15488  0 
arc4                    3456  0 
ecb                     5248  0 
snd_hda_intel         440408  3 
blkcipher               9476  1 ecb
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
snd_pcm                92168  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_hwdep              12552  1 snd_hda_intel
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
snd_seq_midi           10688  0 
snd_rawmidi            29856  1 snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
ide_cd                 35488  1 
cdrom                  41512  1 ide_cd
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fglrx                1804800  26 
snd_timer              27912  2 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               9092  0 
video                  23444  0 
output                  5632  1 video
sdhci                  21508  0 
snd                    70856  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
battery                16776  0 
psmouse                46236  0 
mmc_core               59272  1 sdhci
ricoh_mmc               5120  0 
wmi_acer               11076  0 
pata_atiixp            10496  0 
pata_acpi               9856  0 
ata_generic             9988  0 
i2c_piix4              11148  0 
ac                      8328  0 
button                 10912  0 
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
dcdbas                 11312  0 
i2c_core               28544  1 i2c_piix4
soundcore              10400  1 snd
evdev                  14976  7 
k8temp                  7680  0 
pcspkr                  4992  0 
ext3                  149264  1 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
sg                     41880  0 
sd_mod                 33280  3 
ehci_hcd               41996  0 
ohci_hcd               27524  0 
atiixp                  6672  0 [permanent]
ide_core              136600  2 ide_cd,atiixp
usbcore               169904  4 ndiswrapper,ehci_hcd,ohci_hcd
ahci                   33028  2 
libata                176432  4 pata_atiixp,pata_acpi,ata_generic,ahci
scsi_mod              178488  3 sg,sd_mod,libata
thermal                19744  0 
processor              41448  2 powernow_k8,thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  3 

```

---

### Post by maartsen on 2008-08-07
:confused::confused:

This just does not make sense. The powernow_k8 is normally only used for AMD Athlon64 or higher and not for an Intel processor.

And if I try to insert the module, this tells me ```
"FATAL: Error inserting powernow_k8 (/lib/modules/2.6.24-19-generic/kernel/arch/x86/kernel/cpu/cpufreq/powernow-k8.ko): No such device"
```

So what kind of kernel are you using??

---

### Post by terry f on 2008-08-07
I am sorry the compute I ran that on does have a AMD Athlon 64bit X2 I will try to post for the ATOM latter to day.

---

### Post by ahbart on 2008-08-13
Maybe I can help you with this, if that is still needed.
The output of lsmod:
```

Module                  Size  Used by
af_packet              23044  4 
ipv6                  268292  10 
i915                   31744  3 
drm                    81556  4 i915
rfcomm                 41104  2 
l2cap                  24832  13 rfcomm
bluetooth              60388  4 rfcomm,l2cap
ppdev                   9604  0 
acpi_cpufreq            9876  0 
cpufreq_userspace       4396  0 
cpufreq_stats           6284  0 
cpufreq_powersave       1920  0 
cpufreq_ondemand        8972  2 
freq_table              4744  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     7944  0 
sbs                    14344  0 
sbshc                   6912  1 sbs
dock                   10512  0 
container               4864  0 
iptable_filter          3072  0 
ip_tables              14028  1 iptable_filter
x_tables               15364  1 ip_tables
ext3                  135944  1 
jbd                    47380  1 ext3
parport_pc             35492  0 
lp                     11556  0 
parport                37064  3 ppdev,parport_pc,lp
evdev                  12160  6 
psmouse                44180  0 
uvcvideo               58248  0 
serio_raw               7172  0 
compat_ioctl32          1536  1 uvcvideo
snd_hda_intel         346128  3 
videodev               28544  1 uvcvideo
snd_pcm_oss            41248  0 
v4l1_compat            14724  2 uvcvideo,videodev
v4l2_common            17664  2 uvcvideo,videodev
snd_mixer_oss          17024  1 snd_pcm_oss
snd_pcm                77572  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         10632  2 snd_hda_intel,snd_pcm
snd_hwdep               9732  1 snd_hda_intel
pcspkr                  3456  0 
rt2860sta             524120  1 
snd_seq_dummy           4100  0 
atl1e                  35092  0 
battery                13444  0 
snd_seq_oss            34560  0 
ac                      6148  0 
video                  19088  0 
output                  3968  1 video
snd_seq_midi            8480  0 
snd_rawmidi            24864  1 snd_seq_midi
eeepc_acpi              7824  0 
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
iTCO_wdt               12196  0 
iTCO_vendor_support     4100  1 iTCO_wdt
snd_seq                53200  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
button                  8464  0 
intel_agp              24724  1 
snd_timer              23940  2 snd_pcm,snd_seq
snd_seq_device          8716  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
agpgart                33864  3 drm,intel_agp
snd                    55972  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8032  1 snd
shpchp                 33428  0 
pci_hotplug            14728  1 shpchp
ext2                   72456  1 
mbcache                 8704  2 ext3,ext2
usbhid                 31616  0 
hid                    38144  1 usbhid
usb_storage            72640  1 
libusual               18340  1 usb_storage
sg                     36240  0 
sd_mod                 29952  4 
ata_piix               18948  1 
pata_acpi               7552  0 
ata_generic             7556  0 
libata                158576  3 ata_piix,pata_acpi,ata_generic
scsi_mod              150796  4 usb_storage,sg,sd_mod,libata
ehci_hcd               37388  0 
uhci_hcd               26256  0 
usbcore               145644  7 uvcvideo,usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                16028  0 
processor              36672  4 acpi_cpufreq,thermal
fan                     4868  0 
fuse                   49812  3 

```

This is on my Asus EEEpc 901 Atom 1.6. CPU scaling is working with the above howto (dpkg-reconfigure gnome-applets)
I've ubuntu 8.04.1 installled with the 2.6.24-21-eeepc from:
[Array.org]("http://www.array.org/ubuntu/index.html")

I'll hope this will help you or others.

---

### Post by vishnumrao on 2009-08-25
> **maartsen said:**
> Hi there,

I've installed Ubuntu 8.04 LTS on my server (which is an Intel Atom D945GCLF).

If I try to startup powernowd i get this:
[FONT="Courier New"]
 * Starting powernowd...
 * CPU frequency scaling not supported...                                [ OK ][/FONT]

So I've checked if the modules are loaded, but I cannot load the speedstep centrino modules (or any speedstep module for that fact). It gives a "no such device" error.

The question is now. Has somebody got a working configuration for cpu throttling with the Intel Atom?

maartsen, 

Have you been able to get frequency scaling working? Please see this link: [http://ubuntuforums.org/showthread.php?t=1104619&highlight=330+frequency+scaling](http://ubuntuforums.org/showthread.php?t=1104619&highlight=330+frequency+scaling)

There is one post with a link to intel website. Looks like frequency scaling is not supported on Atom 230 and Atom 330, which are desktop/nettop procesors, while Atom 270 and Atom 280 are mobile/netbook processors.

Could you update the thread if you have had any luck with scaling.

---

### Post by Anita_Tsai on 2009-08-25
Could you tell us the methods you have been used to figure it?

There are some settings on BIOS, on the OS about that problem.

But basically, the laptop can change the frequency itself.

---

