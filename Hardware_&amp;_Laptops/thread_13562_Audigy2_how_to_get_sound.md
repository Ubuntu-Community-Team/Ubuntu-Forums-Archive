---
title: "Audigy2 how to get sound?"
date: 2005-02-01
forum: Hardware &amp; Laptops
---

### Post by Zillion on 2005-02-01
Hi I read and read about sound here but i dont understand it, could someplz explain me in noob terms how I can get sound with my audigy2?

The volume mixer shows Audigy2 and all the controls but I hear no sound when using for example xmms. 

The only sound I hear is a beep when logging in.

I tried 

sudo /etc/init.d/alsa stop
deleted var/lib/alsa/asound.state
and started alsa again w/ sudo /etc/init.d/alsa start.


I read something about including lsmod, i see there something about ac97 onboard sound, could that have something to do with it? but I disabled it in bios before installation.

here is the lsmod

Module                  Size  Used by

proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
button                  6936  0
ac                      5132  0
battery                 9740  0
ipv6                  230020  8
af_packet              20872  2
emu10k1_gp              3840  0
snd_emu10k1            80776  4
snd_ac97_codec         59268  1 snd_emu10k1
snd_util_mem            4608  1 snd_emu10k1
snd_hwdep               9120  1 snd_emu10k1
ohci1394               32004  0
3c59x                  36776  0
usblp                  12032  0
shpchp                 87276  0
pciehp                 83948  0
pci_hotplug            30640  2 shpchp,pciehp
forcedeth              16128  0
ehci_hcd               27780  0
snd_usb_audio          65120  0
snd_rawmidi            23232  2 snd_emu10k1,snd_usb_audio
snd_seq_device          7944  2 snd_emu10k1,snd_rawmidi
snd_pcm_oss            48168  0
snd_mixer_oss          16640  1 snd_pcm_oss
snd_pcm                85540  3 snd_emu10k1,snd_usb_audio,snd_pcm_oss
snd_page_alloc         11144  2 snd_emu10k1,snd_pcm
snd_timer              23172  1 snd_pcm
snd                    50660  19 snd_emu10k1,snd_ac97_codec,snd_util_mem,snd_hwd ep,snd_usb_audio,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,sn d_timer
pwc                    48240  0
videodev                9856  1 pwc
audio                  42240  4
soundcore               9824  6 snd,audio
ohci_hcd               19460  0
usbcore               104292  8 usblp,ehci_hcd,snd_usb_audio,pwc,audio,ohci_hcd
nvidia_agp              7580  1
agpgart                31784  1 nvidia_agp
analog                 10784  0
gameport                4736  2 emu10k1_gp,analog
floppy                 54996  0
pcspkr                  3816  0
rtc                    12216  0
ntfs                   88660  1
nls_iso8859_1           4352  1
nls_cp437               6016  2
vfat                   13312  1
fat                    41792  1 vfat
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
sbp2                   22408  0
ieee1394              100536  2 ohci1394,sbp2
tsdev                   7168  0
evdev                   9088  0
ide_cd                 38276  0
mousedev               10124  1
psmouse                17800  0
sr_mod                 15780  0
scsi_mod              115148  2 sbp2,sr_mod
cdrom                  35872  2 ide_cd,sr_mod
ext3                  109544  0
jbd                    54552  1 ext3
ide_generic             1664  0
ide_disk               16768  6
amd74xx                13340  1
ide_core              125272  4 ide_cd,ide_generic,ide_disk,amd74xx
unix                   25904  736
fan                     4236  0
thermal                13200  0
processor              17712  1 thermal
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb

---

### Post by Zillion on 2005-02-01
ah I found the problem!  in my volume controls it stated also a "USB audio class driver [OSS mixer]" which appeared to be a usb logitech webcam with a mic in it. after unplugging the webcam and restarting my PC I had sound! I hope this may help others.

edit.. after restarting again suddenly I also had ac97 controls besided audigy2.. which resulted in no sound again.. but then I read the post from mrv how to bypass this [http://ubuntuforums.org/showthread.php?t=3898](http://ubuntuforums.org/showthread.php?t=3898)

if anyone knows how i can use the webcam at the same time with my soundcard.. tx

---

### Post by swingincelt on 2005-02-03
This process of adding the soundcard module to /etc/modules worked for me.

[http://www.ubuntuforums.org/showthread.php?p=55102](http://www.ubuntuforums.org/showthread.php?p=55102)

Sucks though because up to just a few days ago I didn't need this hack and my devices all got initialized in the correct order.

Cheers,
Swingincelt

---

### Post by HiddenWolf on 2005-02-04
[QUOTE=swingincelt]This process of adding the soundcard module to /etc/modules worked for me.

[http://www.ubuntuforums.org/showthread.php?p=55102](http://www.ubuntuforums.org/showthread.php?p=55102)

Sucks though because up to just a few days ago I didn't need this hack and my devices all got initialized in the correct order.

Cheers,
Swingincelt[/QUOTE]
using hoary?

---

