---
title: "Acer laptop heating up!"
date: 2005-05-30
forum: Hardware &amp; Laptops
---

### Post by recmar on 2005-05-30
Hello!
Cooling fan on my Acer turns on every 30 sec. during standard jobs (browsing the web, editing  documents). On SuSE and few other distros I didn't have this kind issue. Wher can be the problem?

---

### Post by ::DoGG:: on 2005-05-30
Could You send the output of lsmod command ? Do you have all the "laptop necessary" module loaded ? ( acpi,thermal, battery, ac ....)

---

### Post by ssck on 2005-05-30
Hi ALL,

I am also using an Acer Travelmate 2300.Could anyone teach me how to read the settings in lsmod ?

Module                  Size  Used by
speedstep_lib           4228  0
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
pcmcia                 21380  2
ipt_limit               2688  8
iptable_mangle          2944  0
ipt_LOG                 6656  8
ipt_MASQUERADE          3584  0
iptable_nat            24648  1 ipt_MASQUERADE
ipt_TOS                 2560  0
ipt_REJECT              6528  1
ip_conntrack_irc       71856  0
ip_conntrack_ftp       72624  0
ipt_state               2048  6
ip_conntrack           43668  5 ipt_MASQUERADE,iptable_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
iptable_filter          3840  1
ip_tables              17408  9 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,iptable_nat,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
i915                   18304  1
drm                    59412  2 i915
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
ipv6                  229504  9
yenta_socket           19584  0
pcmcia_core            53568  2 pcmcia,yenta_socket
b44                    20356  0
mii                     4736  1 b44
snd_intel8x0           29984  2
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
i2c_i801                8076  0
i2c_core               21264  1 i2c_i801
hw_random               5524  0
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
usbhid                 29376  0
ehci_hcd               29444  0
uhci_hcd               30224  0
usbcore               107384  4 usbhid,ehci_hcd,uhci_hcd
intel_agp              20636  1
agpgart                31784  3 drm,intel_agp
rtc                    12216  0
md                     43856  0
evdev                   9088  1
joydev                  9408  0
dm_mod                 53116  1
tsdev                   7488  0
capability              5000  0
commoncap               7808  1 capability
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  0
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  1 ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
piix                    9988  1
ide_disk               18176  3
ide_core              118988  4 ide_cd,ide_generic,piix,ide_disk
unix                   26164  901
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

I have some problems using Ubuntu with it :

1) The touchpad is not working
2) The battery indicator is wrong

Not sure if the speedstep and fan is working as it should be.

Could someone teach me ?

All help appreciated.

Thanks.

---

### Post by ::DoGG:: on 2005-05-31
with touchpad try to reload modules by hand:

```
rmmod evdev
rmmod tsdev
rmmod psmouse

modprobe tsdev
modporbe evdev
modprobe psmouse
```

should work if you are using /dev/input/mice device in xorg.conf ( i guess you are using synaptics touchpad)

---

### Post by recmar on 2005-05-31
O.K
This is my lsmod. See anything interesting?

:~$ lsmod
Module                  Size  Used by
nls_utf8                2176  1
nls_cp437               5888  1
vfat                   12928  1
fat                    37792  1 vfat
sd_mod                 16784  2
usb_storage            64064  1
ipv6                  229504  6
powernow_k7             8744  0
proc_intf               4100  0
cpufreq_powersave       1920  0
cpufreq_userspace       4572  1
cpufreq_ondemand        6172  0
freq_table              4100  1 powernow_k7
pcmcia                 21380  2
video                  16260  0
battery                10244  0
container               4608  0
button                  6800  0
pcc_acpi               11264  0
sony_acpi               6280  0
ac                      4996  0
via_rhine              19972  0
mii                     4736  1 via_rhine
slamr                 376132  0
snd_via82xx            25248  2
snd_ac97_codec         64608  1 snd_via82xx
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  2 snd_via82xx,snd_pcm
gameport                4608  1 snd_via82xx
snd_mpu401_uart         7168  1 snd_via82xx
snd_rawmidi            22944  1 snd_mpu401_uart
snd_seq_device          8332  1 snd_rawmidi
snd                    50276  9 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  3 snd
i2c_viapro              7436  0
i2c_core               21264  1 i2c_viapro
usbhid                 29376  0
via_ircc               24340  0
irda                  168000  1 via_ircc
crc_ccitt               2176  1 irda
ehci_hcd               29444  0
uhci_hcd               30224  0
usbcore               107384  5 usb_storage,usbhid,ehci_hcd,uhci_hcd
ohci1394               31876  0
yenta_socket           19584  0
pcmcia_core            53568  2 pcmcia,yenta_socket
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
via_agp                 9216  1
agpgart                31784  1 via_agp
floppy                 54864  0
pcspkr                  3816  0
rtc                    12216  0
md                     43856  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
sr_mod                 16036  0
sbp2                   22408  0
scsi_mod              119936  4 sd_mod,usb_storage,sr_mod,sbp2
tsdev                   7488  0
ieee1394              100408  2 ohci1394,sbp2
joydev                  9408  0
evdev                   9088  1
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  2 sr_mod,ide_cd
reiserfs              225616  2
ext3                  120968  0
jbd                    54168  1 ext3
ide_generic             1664  0
ide_disk               18176  4
via82cxxx              12956  1
ide_core              118988  5 usb_storage,ide_cd,ide_generic,ide_disk,via82cxxx
unix                   26164  894
thermal                13576  0
processor              22708  2 powernow_k7,thermal
fan                     4612  0
fbcon                  34048  71
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  1
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

---

### Post by ::DoGG:: on 2005-06-01
Well... in shell type:
```
modprobe acpi
```
or
```
modprobe apm
```

but i would recommend You acpi, newer...
above code will load acpi module, responsible for all the heating-power-battery deal in linux.

P.S. How`s the touchpad ?

---

