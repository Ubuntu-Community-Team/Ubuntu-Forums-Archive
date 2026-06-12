---
title: "No sound (asus a8n-sli deluxe onboard)"
date: 2007-10-14
forum: Hardware &amp; Laptops
---

### Post by crispy_chunks on 2007-10-14
I recently got my greedy hands on some new hardware so i could play around with compiz. I installed the gutsy gibbon  beta and compiz worked out of the box. However, my sound did not work. It appears that ubuntu installed the drivers correctly (it found the realtek 850 chip) but there is no sound!

So far ive checked cables and unmuted all channels in alsa, i have also tried several players to play back some audio.

lsmod
```

Module                  Size  Used by
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8072  0 
cpufreq_powersave       2688  0 
sbs                    19592  0 
ac                      6148  0 
container               5504  0 
button                  8976  0 
video                  18060  0 
dock                   10656  0 
battery                11012  0 
it87                   19856  0 
hwmon_vid               4352  1 it87
i2c_isa                 5248  1 it87
sbp2                   24072  0 
lp                     12580  0 
nvidia               6221648  34 
agpgart                35016  1 nvidia
snd_mpu401              9640  0 
snd_mpu401_uart         9600  1 snd_mpu401
analog                 13344  0 
parport_pc             37412  1 
snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
parport                37448  3 ppdev,lp,parport_pc
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  2 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
gameport               16776  1 analog
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0 
psmouse                39952  0 
serio_raw               8068  0 
snd                    54660  12 snd_mpu401,snd_mpu401_uart,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  2 snd
k8temp                  6656  0 
i2c_nforce2             7040  0 
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
i2c_core               26112  4 it87,i2c_isa,nvidia,i2c_nforce2
ipv6                  274020  12 
evdev                  11136  3 
ext3                  133768  4 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_disk               18304  8 
floppy                 60004  0 
forcedeth              51592  0 
amd74xx                15260  0 [permanent]
ide_core              116548  2 ide_disk,amd74xx
skge                   43152  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
sata_nv                20612  0 
ata_generic             8452  0 
libata                124528  2 sata_nv,ata_generic
scsi_mod              147084  2 sbp2,libata
ehci_hcd               36108  0 
ohci_hcd               22916  0 
usbcore               138248  3 ehci_hcd,ohci_hcd
thermal                14344  0 
processor              31944  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40600  0 
commoncap               8320  1 apparmor

```

---

### Post by punkybouy on 2007-10-14
Create a new user and then log in as that user and see if they have sound.

---

### Post by crispy_chunks on 2007-10-15
Still same problem with the new user.

Also tried to run apps as sudo if the device was root only ;>

---

### Post by otac0n on 2007-10-23
I'm having the same issue...

Any luck?

---

### Post by crispy_chunks on 2008-01-14
Bumping!

Well as of now im just using my old Aureal card which works fine, but ive bought a surround system, and therefore i need to get the onboard sound working.

First of all, i can only get my aureal card playing (of course), but i cant even get it to stop playing! Which means i dont know how to get the system to at least try to use the onboard sound. How would i fix this? How do i get alsa to user the onboard sound instead of the aureal card?

If i can get this fixed i can continue troubleshooting my surround sound.

Any help appreciated!

---

### Post by crispy_chunks on 2008-01-17
I now know whats wrong. The onboard sound card is only outputting on the digital port - maybe this info will help someone solve their problem. I dont have any problems now since i recently bought a reciever with digi input :p

---

