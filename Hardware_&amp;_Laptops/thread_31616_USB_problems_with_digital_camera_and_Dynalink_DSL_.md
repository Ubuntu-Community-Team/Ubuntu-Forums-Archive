---
title: "USB problems with digital camera and Dynalink DSL modem"
date: 2005-05-04
forum: Hardware &amp; Laptops
---

### Post by mpt on 2005-05-04
My digital camera used to appear on the desktop when I plugged it in to the USB port on this Toshiba Satellite laptop. About a week ago, that stopped happening. (CDs also stopped appearing in Nautilus, despite "Mount removable media when inserted" being turned on, though that may be a separate problem.) lsusb shows "Bus 003 Device 002: ID 0a17:001f Pentax Corp.", but gThumb says "No camera detected" (whereas it used to offer to import my photos whenever I plugged the camera in).

A similar thing happens when I plug in my Dynalink UD800G3 Home DSL modem: lsusb reports "Bus 003 Device 003: ID 0915:8102 GlobeSpan, Inc.", but Gnome PPP and pppoeconf both say "No modem was found on your system", even after installing pppoe, and after installing and configuring the [Eciadsl driver](http://eciadsl.flashtux.org/index.php?lang=en) for Globespan-based modems.

Are these problems related? What should I do next? Thanks for any help.

Following the suggestion in [another thread](http://www.ubuntuforums.org/showthread.php?t=24150&highlight=usb+modem), here's the output of lsmod:
```

Module                  Size  Used by
speedstep_centrino      7892  1
proc_intf               4100  0
freq_table              4100  1 speedstep_centrino
cpufreq_userspace       4572  1
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
pcmcia                 21380  2
i915                   18304  1
drm                    59412  2 i915
video                  16260  0
toshiba_acpi            9388  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
ipv6                  229376  15
af_packet              20744  2
yenta_socket           19584  0
pcmcia_core            53568  2 pcmcia,yenta_socket
e100                   32384  0
mii                     4736  1 e100
ohci1394               31876  0
ipw2200                66156  0
firmware_class          9728  1 ipw2200
ieee80211              21252  1 ipw2200
ieee80211_crypt         5832  1 ieee80211
snd_intel8x0           29984  2
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
pci_hotplug            30512  0
ehci_hcd               29444  0
uhci_hcd               30224  0
usbcore               107384  3 ehci_hcd,uhci_hcd
intel_agp              20508  1
agpgart                31784  3 drm,intel_agp
rtc                    12216  0
pcspkr                  3816  0
md                     43728  0
dm_mod                 53116  1
evdev                   9088  0
capability              5000  0
tsdev                   7488  0
commoncap               7808  1 capability
sr_mod                 16036  0
sbp2                   22408  0
scsi_mod              120064  2 sr_mod,sbp2
ieee1394              100408  2 ohci1394,sbp2
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  0
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  2 sr_mod,ide_cd
ext3                  120200  2
jbd                    53912  1 ext3
ide_generic             1664  0
piix                    9988  1
ide_disk               18176  4
ide_core              118988  4 ide_cd,ide_generic,piix,ide_disk
unix                   26164  997
thermal                13576  0
processor              22708  2 speedstep_centrino,thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

```

---

### Post by poofyhairguy on 2005-05-04
[QUOTE=mpt] gThumb says "No camera detected" (whereas it used to offer to import my photos whenever I plugged the camera in).[/QUOTE]

try it when you run gthumb with this command:

gksudo gthumb

---

### Post by mpt on 2005-05-04
> gksudo gthumbExactly the same result. Thanks for the suggestion, though.

(Getting my modem working is actually more urgent, because I'm supposed to be working from home.)

---

