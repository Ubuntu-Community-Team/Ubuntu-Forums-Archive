---
title: "Nforce 3, nvsound, ALSA apps broken?"
date: 2005-04-03
forum: Hardware &amp; Laptops
---

### Post by Armourer on 2005-04-03
Well, I just upgraded from an old via board to a new Neo 2 Platinum (Nforce 3)
board.
After a little research, I downloaded and installed the NForce-0331 drivers.
I rebooted, and with the exception of the superloud gnome startup noise, system sounds are fine, games like et and ut2004 work,
but any alsa based audio player, like rythmbox and totem complain about lacking an installed ALSA card, and Macromedia Flash 7 sounds absolutely atrocious (crackly and the like) :(

lsmod returns these modules-
Module                  Size  Used by
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
snd_pcm_oss            48296  0
snd_mixer_oss          16640  1 snd_pcm_oss
snd_via82xx            26660  0
button                  6936  0
ac                      5132  0
battery                 9740  0
ipv6                  230148  79
af_packet              20872  2
r8169                  16004  0
crc32                   4608  1 r8169
ohci1394               32004  0
ieee1394              100536  1 ohci1394
sd_mod                 20480  0
sata_nv                 8324  0
libata                 36356  1 sata_nv
scsi_mod              115148  2 sd_mod,libata
snd_intel8x0           33068  0
snd_ac97_codec         59268  2 snd_via82xx,snd_intel8x0
snd_pcm                85540  3 snd_pcm_oss,snd_via82xx,snd_intel8x0
snd_timer              23300  1 snd_pcm
snd_page_alloc         11144  3 snd_via82xx,snd_intel8x0,snd_pcm
gameport                4736  2 snd_via82xx,snd_intel8x0
snd_mpu401_uart         7296  2 snd_via82xx,snd_intel8x0
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  1 snd_rawmidi
snd                    50660  10 snd_pcm_oss,snd_mixer_oss,snd_via82xx,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
nvsound              1539864  2
soundcore               9824  4 snd,nvsound
forcedeth              16128  0
ehci_hcd               27780  0
usblp                  12032  1
tsdev                   7168  0
joydev                  9536  0
usbhid                 28864  0
ohci_hcd               19460  0
usbcore               104292  7 ehci_hcd,usblp,usbhid,ohci_hcd
amd64_agp              10696  1
agpgart                31784  1 amd64_agp
floppy                 54996  0
pcspkr                  3816  0
rtc                    12216  0
vfat                   13312  0
fat                    41792  1 vfat
isofs                  33848  0
udf                    79876  0
nls_cp437               6016  1
ntfs                   88660  1
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
loop                   14728  0
nvidia               4821556  12
evdev                   9216  0
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
ide_cd                 38276  0
cdrom                  35872  1 ide_cd
mousedev               10124  1
psmouse                17800  0
ext3                  109672  2
jbd                    54552  1 ext3
ide_generic             1664  0
ide_disk               16768  6
amd74xx                13340  1
ide_core              125272  4 ide_cd,ide_generic,ide_disk,amd74xx
unix                   26160  715
fan                     4236  0
thermal                13200  0
processor              17712  1 thermal
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb

What concerns me is that not only is nvsound loaded, but so is snd_intel8x0, and snd_via82xx too!

1. Is there anyway to get ALSA applications and Flash Player working with nvsound?
2. Should I remove the extra modules, and if so, how?

Thanks all, 
Evan

---

### Post by Armourer on 2005-04-03
[QUOTE=Armourer]Well, I just upgraded from an old via board to a new Neo 2 Platinum (Nforce 3)
board.
After a little research, I downloaded and installed the NForce-0331 drivers.
I rebooted, and with the exception of the superloud gnome startup noise, system sounds are fine, games like et and ut2004 work,
but any alsa based audio player, like rythmbox and totem complain about lacking an installed ALSA card, and Macromedia Flash 7 sounds absolutely atrocious (crackly and the like) :(

lsmod returns these modules-
Module                  Size  Used by
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
snd_pcm_oss            48296  0
snd_mixer_oss          16640  1 snd_pcm_oss
snd_via82xx            26660  0
button                  6936  0
ac                      5132  0
battery                 9740  0
ipv6                  230148  79
af_packet              20872  2
r8169                  16004  0
crc32                   4608  1 r8169
ohci1394               32004  0
ieee1394              100536  1 ohci1394
sd_mod                 20480  0
sata_nv                 8324  0
libata                 36356  1 sata_nv
scsi_mod              115148  2 sd_mod,libata
snd_intel8x0           33068  0
snd_ac97_codec         59268  2 snd_via82xx,snd_intel8x0
snd_pcm                85540  3 snd_pcm_oss,snd_via82xx,snd_intel8x0
snd_timer              23300  1 snd_pcm
snd_page_alloc         11144  3 snd_via82xx,snd_intel8x0,snd_pcm
gameport                4736  2 snd_via82xx,snd_intel8x0
snd_mpu401_uart         7296  2 snd_via82xx,snd_intel8x0
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  1 snd_rawmidi
snd                    50660  10 snd_pcm_oss,snd_mixer_oss,snd_via82xx,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
nvsound              1539864  2
soundcore               9824  4 snd,nvsound
forcedeth              16128  0
ehci_hcd               27780  0
usblp                  12032  1
tsdev                   7168  0
joydev                  9536  0
usbhid                 28864  0
ohci_hcd               19460  0
usbcore               104292  7 ehci_hcd,usblp,usbhid,ohci_hcd
amd64_agp              10696  1
agpgart                31784  1 amd64_agp
floppy                 54996  0
pcspkr                  3816  0
rtc                    12216  0
vfat                   13312  0
fat                    41792  1 vfat
isofs                  33848  0
udf                    79876  0
nls_cp437               6016  1
ntfs                   88660  1
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
loop                   14728  0
nvidia               4821556  12
evdev                   9216  0
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
ide_cd                 38276  0
cdrom                  35872  1 ide_cd
mousedev               10124  1
psmouse                17800  0
ext3                  109672  2
jbd                    54552  1 ext3
ide_generic             1664  0
ide_disk               16768  6
amd74xx                13340  1
ide_core              125272  4 ide_cd,ide_generic,ide_disk,amd74xx
unix                   26160  715
fan                     4236  0
thermal                13200  0
processor              17712  1 thermal
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb

What concerns me is that not only is nvsound loaded, but so is snd_intel8x0, and snd_via82xx too!

1. Is there anyway to get ALSA applications and Flash Player working with nvsound?
2. Should I remove the extra modules, and if so, how?

Thanks all, 
Evan[/QUOTE]
 Ok, after doing a bit more searching, I ran gstreamer-properties, and switched output to OSS.
Sound apps like totem and ryhthmbox check out!
yay!
Flash....ack
no, flashplayer is still brutally violated by horrible, crackly audio death...
Why oh why?

---

