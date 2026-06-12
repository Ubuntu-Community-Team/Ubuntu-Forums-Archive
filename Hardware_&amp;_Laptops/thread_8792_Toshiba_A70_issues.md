---
title: "Toshiba A70 issues"
date: 2004-12-21
forum: Hardware &amp; Laptops
---

### Post by safecracker on 2004-12-21
I have a Toshiba A70 with a ALPS touchpad and Realtek ALC259 sound card. I can't get either to work and need help resolving the issue. the following is the output of lsmod

Module                  Size  Used by
acpi                    5996  0
proc_intf               3776  0
cpufreq_powersave       1728  0
cpufreq_userspace       5240  2
freq_table              4196  1 acpi
ds                     18436  2
button                  6584  0
ac                      4812  0
battery                 9388  0
ipv6                  257028  17
af_packet              22088  4
yenta_socket           20992  1
pcmcia_core            68404  2 ds,yenta_socket
8139cp                 20256  0
8139too                25568  0
mii                     5056  2 8139cp,8139too
crc32                   4288  2 8139cp,8139too
ath_pci                55812  0
wlan                  117500  3 ath_pci
ath_hal               129264  3 ath_pci
ohci1394               34884  0
snd_atiixp             21160  0
snd_ac97_codec         67844  1 snd_atiixp
snd_pcm_oss            52968  0
snd_mixer_oss          19456  1 snd_pcm_oss
snd_pcm                95140  2 snd_atiixp,snd_pcm_oss
snd_timer              24900  1 snd_pcm
snd                    55300  6 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10112  1 snd
snd_page_alloc         11432  2 snd_atiixp,snd_pcm
ehci_hcd               30756  0
joydev                  9728  0
tsdev                   7232  0
usbhid                 31392  0
ohci_hcd               20996  0
usbcore               115684  5 ehci_hcd,usbhid,ohci_hcd
pciehp                 96108  0
shpchp                 99340  0
pci_hotplug            33680  2 pciehp,shpchp
ati_agp                 8460  1
agpgart                33640  1 ati_agp
irtty_sir               8960  0
sir_dev                18924  1 irtty_sir
irda                  191328  2 irtty_sir,sir_dev
crc_ccitt               2112  1 irda
pcspkr                  3592  0
rtc                    12536  0
md                     48552  0
dm_mod                 57308  1
capability              4520  0
commoncap               7072  1 capability
parport_pc             34752  1
evdev                   9440  0
lp                     10724  0
parport                40712  2 parport_pc,lp
sbp2                   23816  0
ieee1394              108408  2 ohci1394,sbp2
ide_cd                 41572  0
mousedev               10220  1
psmouse                19720  0
sr_mod                 16900  0
scsi_mod              122508  2 sbp2,sr_mod
cdrom                  39392  2 ide_cd,sr_mod
reiserfs              240880  1
ext2                   69960  0
ext3                  123880  0
jbd                    60824  1 ext3
mbcache                 9092  2 ext2,ext3
ide_generic             1408  0
ide_disk               18752  3
atiixp                  8696  1
ide_core              136120  4 ide_cd,ide_generic,ide_disk,atiixp
unix                   28304  735
fan                     3980  0
thermal                12976  0
processor              17392  2 acpi,thermal
font                    8352  0
vesafb                  6560  0
cfbcopyarea             3712  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3616  1 vesafb
 
The card shows up in in the device manager as "IXP150 AC'97 Audio Controller".

I think it is a issue with ALSA due to alsaconf returning "command not found" and alsamixer returning " function snd_ctl_open failed for default: No such device". The alsamixer error does this due to no card being reconized if I'm not mistaken.

Now for the 2nd issue. Is it possible to get my touchpad woking without doing a recompile of my kernel and X?

---

### Post by safecracker on 2004-12-22
After surfing some more I found SuSE uses the snd_atiixp module to correctly locate the soundcard.......as you can see from above it is loading in ubuntu but still no sound.....anyone have an idea?

---

### Post by Jspired on 2004-12-22
I can't help you, but there's a thread here about your laptop and this issue:  [IMG]http://www.ubuntuforums.org/showthread.php?t=3470&highlight=Toshiba+Satellite[/IMG]

---

### Post by safecracker on 2004-12-22
[QUOTE=Jspired]I can't help you, but there's a thread here about your laptop and this issue:  [IMG]http://www.ubuntuforums.org/showthread.php?t=3470&highlight=Toshiba+Satellite[/IMG][/QUOTE]

Thanks but that thread still doesn't have a answer. The last post was about a month ago. I seen that thread but figured I would be a lil more specific here. Thanks none the less though.

---

### Post by gregh on 2004-12-27
I also have an A70, he issue with the touchpad (in my case) was that legacy usb support was turned off in the bios.
When I turned this on all worked fine.

-Greg

---

### Post by safecracker on 2004-12-31
[QUOTE=gregh]I also have an A70, he issue with the touchpad (in my case) was that legacy usb support was turned off in the bios.
When I turned this on all worked fine.

-Greg[/QUOTE]

I have legacy usb support enabled in the BIOS, still have the issue though as it was enabled already. Anyone got these 2 issues resolved?

---

### Post by gregh on 2004-12-31
The sound issue can be resolved by downloading "alsa-driver-1.0.6a" (and above) and compiling, make and make install. There is an issue with the kernel that this alsa driver corrects.

[http://www.alsa-project.org/](http://www.alsa-project.org/)

-Greg

---

