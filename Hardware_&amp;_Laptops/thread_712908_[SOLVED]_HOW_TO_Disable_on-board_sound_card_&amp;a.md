---
title: "[SOLVED] HOW TO: Disable on-board sound card &amp;amp;amp; use only the PCI sound card"
date: 2008-03-02
forum: Hardware &amp; Laptops
---

### Post by arimaniac on 2008-03-02
Hello there,

Since this is my first post to this forum because
I am new to Ubuntu [currently using 7.10]
(I was using Debian Linux for 3 years now)
I would like to start my contribution with a HOW TO
on disabling an on-board sound card & installing a PCI sound card.

So lets get started.
**REMARKS**

This how to is not for users that are having a problem installing a sound card!

**PROBLEM:**

When the system recognizes 2 sound cards: 
an **on-board controller** and a **PCI card**
this happens:

The on-board card is selected as default (index=0)
and the PCI as secondary (index=1).

**SOLUTION**

There are 3 ways to solve this problem:
[B][LIST=1]
[*]Disable the card by a jumper on your motherboard.
[*]Disable the card by a BIOS setting.
[*]Disable the card software-wise.
[/LIST][/B]

HOW TO: 

1) Refer your motherboard manual for instruction on how to do this
    [In many cases this is not possible :(  ] 

2) Get in your BIOS and find the option that disables 
    your on board sound card:
    **PROBLEM**
    In my case as in others this does not solve the issue.
    Linux loads the device despite the fact that it appears DISABLED in BIOS,
 
3) a)Open a terminal and type:
```
lsmod
```

**DO NOT TYPE  !!!**
```
sudo aplay -L
```
And use the name of your sound card!
You need the MODULE NAME of your card.

So in my system the output for **lsmod** was:
```
Module                  Size  Used by
ipv6                  273892  8 
af_packet              24840  2 
ppdev                  10244  0 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  0 
cpufreq_conservative     8072  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7232  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
button                  8976  0 
ac                      6148  0 
sbs                    19592  0 
video                  18060  0 
dock                   10656  0 
container               5504  0 
battery                11012  0 
lp                     12580  0 
snd_cmipci              13569  0
snd_emu10k1_synth       8 correction192  0 
snd_emux_synth         35456  1 snd_emu10k1_synth
snd_seq_virmidi         8064  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_emu10k1           137248  2 snd_emu10k1_synth
snd_ac97_codec        100644  1 snd_emu10k1
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
xpad                    9988  0 
snd_pcm                80388  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_emu10k1,snd_pcm
snd_util_mem            5760  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10244  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           4740  0 
usbhid                 29536  0 
snd_seq_oss            33152  0 
hid                    28928  1 usbhid
snd_seq_midi            9600  0 
snd_rawmidi            25728  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      8448  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
nvidia               6221648  34 
via_ircc               27668  0 
serio_raw               8068  0 
psmouse                39952  0 
pcspkr                  4224  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
irda                  202300  1 via_ircc
snd_seq                53232  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9228  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
crc_ccitt               3072  1 irda
i2c_viapro             10004  0 
snd                    54660  15 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
emu10k1_gp              4736  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
i2c_core               26112  2 nvidia,i2c_viapro
via_agp                11264  1 
gameport               16776  2 emu10k1_gp
agpgart                35016  2 nvidia,via_agp
soundcore               8800  1 snd
evdev                  11136  4 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
ide_disk               18560  3 
8139cp                 25088  0 
uhci_hcd               26640  0 
usbcore               138632  4 xpad,usbhid,uhci_hcd
8139too                27776  0 
mii                     6528  2 8139cp,8139too
via82cxxx              10372  0 [permanent]
ide_core              116804  3 ide_cd,ide_disk,via82cxxx
ata_generic             8452  0 
libata                125168  1 ata_generic
scsi_mod              147084  1 libata
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
```

  b) Locate your on board sound card:
      The entry starts with "snd_", in my case its snd_cmipci.
      Copy the module name eg: "snd_cmipci" **AS IS!!!**

  c) Type in terminal:
```
sudo gedit /etc/modprobe.d/blacklist
```

  d) Add the following to the bottom of the file:
```

#Disable the on board sound card so that the PCI can run as default.
blacklist *[module name]* <- in my case snd_cmipci
```

  e) SAVE the file REBOOT the system!

  f) DONE!!! :)

Comments - questions welcome!!!

**02-MAR-08 UPDATE:**

Works on other Debian based distros:
Tested on Debian, Knoppix and Ubuntu
(For other distros inform me if it works...)

---

### Post by Aled Y Cymro on 2008-03-02
It works! Thank you very much for this :D

As you mentioned, changing the BIOS setting didn't work, but this seems to have gotten rid of my onboard soundcard from the devices menu (which was causing my problems).

---

### Post by nonewmsgs on 2008-03-03
i wanted to second what aled said.  disabling the onboard sound in BIOS will affect windows but not Ubuntu.  Ubuntu is so good at handling devices it manages to use it anyway.   

Otherwise This is to quote Bill S. Preston, Esquire, "A most excellent how-to"

---

### Post by arimaniac on 2008-03-03
> **nonewmsgs said:**
> i wanted to second what aled said.  disabling the onboard sound in BIOS will affect windows but not Ubuntu.  Ubuntu is so good at handling devices it manages to use it anyway.   

Otherwise This is to quote Bill S. Preston, Esquire, "A most excellent how-to"

Hi there 

In programming terms this is not entirely true:

Linux kernel bypasses the on/off flag that the BIOS reports
for a device and continues on loading the device in some cases.

Only some BIOS's REALLY disable an on board device
like " cuting off their DC supply " and make it "invisible"
this is because of circuit design restrictions applied by the VLSI laws ...

So its not that Ubuntu is superior, it is just the way Linux works...

Thanks for your comment.

---

### Post by Cubby on 2008-03-05
Thanks, arimaniac!  

Yes, I was one of those that was having problems with this, but I still not sure if it is solved or not for my situation.  I have a Creative:mad:Sound Blaster 24-bit card that is shown as an Audigy family card.  At this thread:

[http://ubuntuforums.org/showthread.php?t=679904&page=4](http://ubuntuforums.org/showthread.php?t=679904&page=4)

 I posted my problems I was having with it under Kubuntu Gutsy Gibbon.  I thought I'd finally gotten everything working with it, and then did several updates and the sound started to emit scratchy and distorted. "Forget this", I thought, so I switched back to Ubuntu, which I had assumed my sound always worked at every boot, and every restart.  I wasn't sure because I don't always have my speakers plugged in, but now I know I have the same problem, though not as bad as with the kubuntu version I was using - sometimes I get sound, sometimes I don't in Ubuntu Feisty Fawn.  

I added the following to my blacklist:
#Disable the on board sound card so that the PCI can run as default.
blacklist snd_mpu401_uart

but today when I restarted, no sound.  

Anyway, thanks for the help.  I'll keep working at it and let you know it I have a more stable outcome.

Update:  For me, your How To only worked at cold boot up of system, but failed each time on restart.  What finally solved my problem was this How To, under, Configuring Default Soundcards [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by erginemr on 2008-03-09
To **arimaniac** -> Thank you for this great howto and your willingness to contribute to the Ubuntu community.

To **Cubby** -> Please refer to this thread:
[http://ubuntuforums.org/showthread.php?p=4481207](http://ubuntuforums.org/showthread.php?p=4481207)

where the tool asoundconf has been proposed to select the default sound card (I didn't try it myself).

---

### Post by arimaniac on 2008-03-14
To Cubby....

Sb Audigy hmmmmmmm....  :-( 
Everytime a person says that he has an audigy there is 
allways trouble.....

ONE NOTE::

DID YOU BLACKLIST THE EXACT NAME OF YOUR CARD"S  MODULE???

snd_xxxxx  

IS DIFFERENT FROM 

snd-xxxx 

AND 

snd-XXxxXX

Be carefull with this... 

PS 

I dont really have any advise on SB Audigy troubleshooting
So goooooooooood luck with this....

Sorry for this delayed reply.....

---

### Post by da Wookiee on 2008-03-15
Trying this on mine, hope it works

---

### Post by da Wookiee on 2008-03-18
Now I have no sound...

:confused:

I blacklisted the onboard sound card and now the Audigy is the only one listed.  I get no sound at all.

lsmod output

```
Module                  Size  Used by
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14080  1 
fat                    54300  1 vfat
af_packet              24840  2 
binfmt_misc            12936  1 
ipv6                  273892  14 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
ppdev                  10244  0 
cpufreq_ondemand        9612  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5280  0 
sbs                    19592  0 
container               5504  0 
ac                      6148  0 
video                  18060  0 
button                  8976  0 
dock                   10656  0 
battery                11012  0 
sbp2                   24072  0 
lp                     12580  0 
snd_emu10k1_synth       8192  0 
snd_emux_synth         35456  1 snd_emu10k1_synth
snd_seq_virmidi         8064  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_emu10k1           137248  2 snd_emu10k1_synth
snd_ac97_codec        100644  1 snd_emu10k1
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_emu10k1,snd_pcm
snd_util_mem            5760  2 snd_emux_synth,snd_emu10k1
sg                     36764  0 
sd_mod                 30336  2 
snd_hwdep              10244  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           4740  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
snd_seq_oss            33152  0 
pcspkr                  4224  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
k8temp                  6656  0 
hci_usb                18332  2 
bluetooth              57060  7 rfcomm,l2cap,hci_usb
agpgart                35016  0 
snd_seq_midi_event      8448  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                53232  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9228  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  15 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
emu10k1_gp              4736  0 
gameport               16776  2 emu10k1_gp
i2c_nforce2             7040  0 
soundcore               8800  1 snd
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
i2c_core               26112  1 i2c_nforce2
evdev                  11136  4 
ext3                  133896  2 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
ide_disk               18560  4 
usb_storage            73024  1 
usbhid                 29536  0 
hid                    28928  1 usbhid
libusual               18448  1 usb_storage
amd74xx                15260  0 [permanent]
ide_core              116804  4 ide_cd,ide_disk,usb_storage,amd74xx
floppy                 60004  0 
forcedeth              51592  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
sata_nv                20612  0 
ehci_hcd               36492  0 
ata_generic             8452  0 
libata                125168  2 sata_nv,ata_generic
scsi_mod              147084  5 sbp2,sg,sd_mod,usb_storage,libata
ohci_hcd               22916  0 
usbcore               138632  7 hci_usb,usb_storage,usbhid,libusual,ehci_hcd,ohci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
```

sudo aplay -L gives


```
default:CARD=Audigy
    Audigy 1 [SB0090], ADC Capture/Standard PCM Playback
    Default Audio Device
front:CARD=Audigy,DEV=0
    Audigy 1 [SB0090], ADC Capture/Standard PCM Playback
    Front speakers
rear:CARD=Audigy,DEV=0
    Audigy 1 [SB0090], ADC Capture/Standard PCM Playback
    Rear speakers
center_lfe:CARD=Audigy,DEV=0
    Audigy 1 [SB0090], ADC Capture/Standard PCM Playback
    Center and Subwoofer speakers
surround40:CARD=Audigy,DEV=0
    Audigy 1 [SB0090], ADC Capture/Standard PCM Playback
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Audigy,DEV=0
    Audigy 1 [SB0090], ADC Capture/Standard PCM Playback
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Audigy,DEV=0
    Audigy 1 [SB0090], ADC Capture/Standard PCM Playback
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Audigy,DEV=0
    Audigy 1 [SB0090], ADC Capture/Standard PCM Playback
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=Audigy,DEV=0
    Audigy 1 [SB0090], ADC Capture/Standard PCM Playback
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
```


I assume I'm still missing something, but what it is I don't know.

---

