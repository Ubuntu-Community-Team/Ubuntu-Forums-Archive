---
title: "Help: /dev/video0 doesn't exist"
date: 2005-06-14
forum: Hardware &amp; Laptops
---

### Post by fourthirtysix on 2005-06-14
Using Ubuntu Linux 5.04, i have successfully compiled the most recent ivtv drivers and it seems to modprobe OK. I created a file called /etc/modutils/ivtv with the following contents:

alias char-major-81 videodev
alias char-major-81-0 ivtv
alias char-major-61 lirc_i2c
options ivtv debug=1
options tuner type=2
options msp3400 once=1 simple=1
add below ivtv msp3400 saa7115 tuner
add above ivtv lirc_dev lirc_i2c




here is the contest of lsmod:




Module                  Size  Used by
bttv                  142928  0
video_buf              20484  1 bttv
btcx_risc               4744  1 bttv
v4l2_common             5888  1 bttv
wm8775                  9624  0
cx25840                39336  0
firmware_class          9728  2 bttv,cx25840
tuner                  19620  0
tveeprom               13620  0
ivtv                 1310884  0
i2c_algo_bit            9224  2 bttv,ivtv
videodev                9728  2 bttv,ivtv
raw1394                28652  0
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
ipv6                  229504  11
af_packet              20744  2
sd_mod                 16784  0
sata_sil                8068  0
libata                 44548  1 sata_sil
sk98lin               149216  0
ohci1394               31876  0
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
snd_intel8x0           29984  1
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
forcedeth              16128  0
ehci_hcd               29444  0
ohci_hcd               19848  0
usbcore               107384  3 ehci_hcd,ohci_hcd
i2c_nforce2             6400  0
i2c_core               21264  7 bttv,wm8775,cx25840,tuner,tveeprom,i2c_algo_bit,i2c_nforce2
nvidia_agp              7452  1
agpgart                31784  1 nvidia_agp
analog                 10784  0
gameport                4608  1 analog
floppy                 54864  0
pcspkr                  3816  0
rtc                    12216  0
md                     43856  0
capability              5000  0
commoncap               7808  1 capability
dm_crypt               11912  0
dm_mod                 53116  2 dm_crypt
aes_i586               39028  0
sr_mod                 16036  0
sbp2                   22408  0
evdev                   9088  0
scsi_mod              119936  4 sd_mod,libata,sr_mod,sbp2
tsdev                   7488  0
ieee1394              100408  3 raw1394,ohci1394,sbp2
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  2 sr_mod,ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
ide_disk               18176  3
amd74xx                13340  1
ide_core              118988  4 ide_cd,ide_generic,ide_disk,amd74xx
unix                   26164  487
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




but the /dev/video0 *still* does not exist.



can anyone help?? thanks!

---

### Post by skoal on 2005-06-14
From what I can tell:
```
skoal@morpheus:///lib/modules/2.6.10-5-686/kernel/drivers/media/video $ strings meye.ko |grep video0
parm=video_nr:video device to register (0=/dev/video0, etc)
```
It would appear that you need to modprobe meye, but when I do that, I get:
```
skoal@morpheus://~ $ sudo modprobe meye
Password:
WARNING: Error inserting sonypi (/lib/modules/2.6.10-5-686/kernel/drivers/char/sonypi.ko): No such device
FATAL: Error inserting meye (/lib/modules/2.6.10-5-686/kernel/drivers/media/video/meye.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```
which indicates I do not have some hardware attached relating to "sonypi" module.  Sorry, but that's about all I could figure...

/edit Oops! I just realized you compiled "ivtv" yourself, and I assume that kernel module should make those /dev entries itself.  My bad.  Must...remember...to...read top sentence of post!

\\//_

---

