---
title: "[SOLVED] WebCam stops working in Gutsy!"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by punong_bisyonaryo on 2007-10-20
Hello all!

I'm sure there's gonna be barrage of <name of device or program> no longer works in Gutsy. Well, my A4Tech Note-Cam Pk35N (ZC0301 in lsmod; Vimicro in Hardware Information) webcam stopped working.

Camorama pops up with a "Could not connect to video device (/dev/video0)", with the debug info switch set, it also says "VIDIOCGCAP  --  could not get camera capabilities, exiting....."

Anybody have an idea on this?

---

### Post by Balazs_noob on 2007-10-20
sorry to bug in to your thread, but i have the same
problem. I  have a A4Tech PK-335MB web cam it worked under
feisty but not under Gutsy , i get the same outputs as you :(

Hope somebody  can help us :)

---

### Post by punong_bisyonaryo on 2007-10-20
I'm glad you dropped by. That's what community is for, so we can help each other out. It's actually good you posted here instead of creating another thread, I believe the driver/chipset of our cams are the same.

Anyway, I was able to get more information, in hopes that it might help someone help us:

Device name (according to camorama): Generic Vimicro 303b
Device driver: gspca

lsmod output in Feisty
```
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
lp                     12452  0 
speedstep_lib           6148  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0 
tc1100_wmi              8068  0 
sony_acpi               6284  0 
pcc_acpi               13184  0 
dev_acpi               12292  0 
video                  16388  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
dock                   10268  0 
container               5248  0 
button                  8720  0 
battery                10756  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
ac                      6020  0 
fuse                   46612  1 
ehci_hcd               34188  0 
uhci_hcd               25360  0 
zc0301                 48516  0 
ipv6                  268704  8 
pcmcia                 39212  0 
snd_intel8x0           34204  1 
snd_ac97_codec         98336  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
joydev                 10816  0 
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
gspca                 607824  0 
videodev               28160  2 zc0301,gspca
v4l2_common            25216  2 zc0301,videodev
v4l1_compat            15236  1 videodev
nsc_ircc               24208  0 
pcspkr                  4224  0 
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
yenta_socket           27532  3 
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
irda                  201276  1 nsc_ircc
crc_ccitt               3072  1 irda
rsrc_nonstatic         14080  1 yenta_socket
sis_agp                 9604  1 
i2c_sis96x              6532  0 
psmouse                38920  0 
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
serio_raw               7940  0 
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
shpchp                 34324  0 
i2c_core               22784  2 i2c_ec,i2c_sis96x
pci_hotplug            32576  1 shpchp
af_packet              23816  2 
agpgart                35400  1 sis_agp
evdev                  11008  4 
tsdev                   8768  0 
squashfs               49028  1 
loop                   17800  2 
unionfs                74020  1 
nls_cp437               6784  1 
isofs                  36284  1 
ext3                  133128  0 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  1 
cdrom                  37664  1 ide_cd
ide_disk               17024  2 
8139too                27648  0 
pata_sis               14220  0 
ata_generic             9092  0 
libata                125720  2 pata_sis,ata_generic
scsi_mod              142348  1 libata
usbhid                 26592  0 
hid                    27392  1 usbhid
sis5513                14856  0 [permanent]
floppy                 59524  0 
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
ohci1394               36528  0 
ieee1394              299448  1 ohci1394
generic                 5124  0 [permanent]
ohci_hcd               22532  0 
usbcore               134280  7 ehci_hcd,uhci_hcd,zc0301,gspca,usbhid,ohci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
```

lsmod output in Gutsy
```
Module                  Size  Used by
nls_iso8859_1           5120  1 
vfat                   14080  1 
fat                    54300  1 vfat
nls_cp437               6784  2 
isofs                  36412  1 
udf                    87204  0 
ipv6                  273892  8 
af_packet              24840  2 
usb_storage            73024  1 
ide_core              116804  1 usb_storage
libusual               18448  1 usb_storage
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
snd_atiixp_modem       17160  0 
snd_via82xx_modem      16264  0 
snd_intel8x0m          18572  5 
speedstep_lib           6404  0 
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
container               5504  0 
asus_acpi              17308  0 
battery                11012  0 
button                  8976  0 
dock                   10656  0 
ac                      6148  0 
sbs                    19592  0 
video                  18060  0 
sbp2                   24072  0 
lp                     12580  0 
gspca                 608336  0 
snd_intel8x0           34972  1 
snd_ac97_codec        100644  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0
ehci_hcd               36492  0 
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  8 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
uhci_hcd               26640  0 
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
joydev                 11328  0 
snd_rawmidi            25728  1 snd_seq_midi
zc0301                 49156  0 
nsc_ircc               24336  0 
compat_ioctl32          2304  1 zc0301
videodev               29312  2 gspca,zc0301
v4l1_compat            15364  1 videodev
v4l2_common            18432  2 zc0301,videodev
irda                  202300  1 nsc_ircc
pcmcia                 41388  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  23 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
crc_ccitt               3072  1 irda
serio_raw               8068  0 
soundcore               8800  1 snd
snd_page_alloc         11400  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_pcm
yenta_socket           27532  3 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                39952  0 
i2c_sis96x              6404  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
sis_agp                10116  1 
agpgart                35016  1 sis_agp
i2c_core               26112  1 i2c_sis96x
evdev                  11136  5 
ext3                  133896  2 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
usbhid                 29536  0 
hid                    28928  1 usbhid
sg                     36764  0 
sr_mod                 17828  1 
cdrom                  37536  1 sr_mod
sd_mod                 30336  6 
8139too                27776  0 
floppy                 60004  0 
pata_sis               15236  4 
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ata_generic             8452  0 
libata                125168  2 pata_sis,ata_generic
scsi_mod              147084  6 usb_storage,sbp2,sg,sr_mod,sd_mod,libata
ohci_hcd               22916  0 
usbcore               138632  9 usb_storage,libusual,gspca,ehci_hcd,uhci_hcd,zc0301,usbhid,ohci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
```

---

### Post by Balazs_noob on 2007-10-21
*bump*

---

### Post by punong_bisyonaryo on 2007-10-21
Found out some more info that I don't know what to do with:

lsusb
```
Bus 001 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam
```

lshw gave nothing relevant to the camera

Weird that gspca is loaded in both Feisty and Gutsy, but why doesn't it work in Gutsy? Not really knowledgable about modules, etc.

Need help please...

---

### Post by bobyy on 2007-10-21
HY 
Just a sugestion...try to install Ekiga , aftre that in the setup pannel you will have  to choice betwen V4L and V4L2 because i see this V4L2 driver it is loaded and the device is recognized..try thys just to see if it is ok ..and your cam.it work.
Good lock.

---

### Post by punong_bisyonaryo on 2007-10-21
> **bobyy said:**
> HY 
Just a sugestion...try to install Ekiga , aftre that in the setup pannel you will have  to choice betwen V4L and V4L2 because i see this V4L2 driver it is loaded and the device is recognized..try thys just to see if it is ok ..and your cam.it work.
Good lock.

Hey, it worked when using the V4L2 driver in Ekiga. So, how can I make it so that all the other applications also know to use the V4L2?

I use Wengo, it can see my webcam, but it isn't able to use it.

---

### Post by bobyy on 2007-10-21
Hy again ..i never use Wengo.. :) try to see the conf file and change the device name(/dev/video0)  with the dev vhat is works in Ekiga

---

### Post by Balazs_noob on 2007-10-21
after Ekiga my webcam works too ;)

thx guys :)

---

### Post by punong_bisyonaryo on 2007-10-22
Hi guys!

@Bobyy
thanks for all your help. But I'm not sure I understand completely. Can I set up v4l2 to be the default for the whole system so that all applications that use webcam will use v4l2? Or do I have to set it specifically for each application?

@Balazs_noob
I would love to know in detail about your results and solutions. Can you please explain to me in detail about your status? Does your camorama now work?

I'm not at home right now so I can't test it right now. I will when I get home in about 6 hours.

Thanks!

---

### Post by Balazs_noob on 2007-10-22
i just followed the Ekiga configuration process
and after that my webcam works in Cheese and
camorama..

if you have at least 1gb you can use a VIrtualBox (Virtual machine)
because in the Virtual XP my webcam works flawlessly ( i need it for msn )

---

### Post by bobyy on 2007-10-22
Hy sorry for delay..
in my vision try to unload V4L1 module ..to force the system to see just V4L2 and hopfully it will work.
I try yesterday Wengophone just with V4L2 and like /dev/video0 and it`s work

regards and good luck.

---

### Post by punong_bisyonaryo on 2007-10-22
I have figured it out!

Simply running Ekiga didn't do it for me. I had to unload the modules in order.
```
sudo modprobe -r gspca
sudo modprobe -r zc0301
sudo modprobe -r videodev
sudo modprobe -r v4l1_compat
```

Now I load them back without the v4l1_compat
```
sudo modprobe gspca
```

It wasn't the v4l1_compat module after all, because it automatically get loaded. What didn't get loaded was the zc0301 module, and it worked when it wasn't loaded!

Woohoo!:D

---

### Post by bobyy on 2007-10-22
Great good job.....damn modules :)

---

### Post by dngpng on 2007-10-24
It works for me, thanks

I only need to remove gspca and zc0301 and reload gspca, since I don't have other 2 modules loaded

---

### Post by Civean on 2007-10-28
I have the same problem under Gutsy with my previously working Kensington KS-1668. This fix does not work for me, though, so this issue isn't solved. Anyone have any ideas?

/C

---

### Post by punong_bisyonaryo on 2007-10-28
Could you put in here the output lsusb and lsmod (and other useful info you may have) so we can have a better clue on how to fix the problem?

---

### Post by Civean on 2007-10-28
I reinstalled gutsy, and voila, it now works flawlessly! The reinstall solved some other minor issues also that i've had for a while. Since I've only been updating, I think a lot of strange stuff carried over since Tribe5 for me =)

/C

---

### Post by zeigfried on 2007-10-28
Hey all,

sudo modprobe -r gspca
sudo modprobe -r zc0301
sudo modprobe  gspca

Worked like a charm, but driver still get load at startup for me.
Adding ```
blacklist zc0301
``` to /etc/modprobe.d/blacklist did the trick.

I hope that helps, this is my first post.

---

### Post by punong_bisyonaryo on 2007-10-29
@Civean
Well whatever works. Glad you got yours working.:)

@Zeigfried
I forgot to post how to blacklist modules. Thanks for putting it up! Hopefully this *fix* will help more people like us.:)

---

### Post by Repgahroll on 2008-01-01
Hello guys! This is my first post here :D

I'm having the same problem... i'm trying to use an A4-Tech PK 335KB, i'm running Gutsy under Fawn kernel (2.6.20-26).

I'm having a very strange experience. Take a look at my steps:

1. Installed gspca module
   - Everything worked fine, camstream, camorama, zoneminder...
2. Afer some time running zoneminder, the computer crashes(first time at ubuntu).
3. Rebooted computer.
   - The camera wasn't working anymore.
4. I'd run modprobe- -r gspca then modprobe gspca.
   - Worked fine using camorama, but when i close it, the camera doesn't work again.
5. Tried about everything, but doesn't work. Removing mods return a fatal error (mod is in use) and --force option doesn't work.

OBS: If i reboot the computer, then run modprobe -r gspca, then modprobe gspca, the camera works again, but just under camorama or camstream or mplayer, and when i close the streaming application, the cam doesn't work anymore. In zoneminder it work just a little time.

Thanks in advance! :D :D :D

---

### Post by hungry on 2008-03-25
> **zeigfried said:**
> Hey all,

sudo modprobe -r gspca
sudo modprobe -r zc0301
sudo modprobe  gspca

Worked like a charm, but driver still get load at startup for me.
Adding ```
blacklist zc0301
``` to /etc/modprobe.d/blacklist did the trick.

I hope that helps, this is my first post.

Thank you!  this worked for my Z-Star Microelectronics Zc0303 Webcam.

---

