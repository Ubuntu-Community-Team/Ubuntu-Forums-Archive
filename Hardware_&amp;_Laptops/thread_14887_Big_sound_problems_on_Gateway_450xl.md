---
title: "Big sound problems on Gateway 450xl"
date: 2005-02-10
forum: Hardware &amp; Laptops
---

### Post by originil on 2005-02-10
Hi all
This is my first post, so please don't hesitate to ask for more information.
I've been a fedora user, but ubuntu looked interesting. I love the distribution, but have a potentially deal-killing problem. 

Sound (onboard (I believe) ESS1988 Allegro-1) has not worked since the install. I tried the liveCD and sound didn't work there either. I've played with the mixers quite a bit, played with gstreamer-properties, and tried installing various alsa related packages, to no avail. 

In gstreamer-properties, when I pick esd for the default audio sink and push test, the test dialog comes up, and the bar moves back and forth but no sound. With this setting, there is absolutely no sound, system, rhythmbox, or games, from what I've tried.

When I select alsa or oss, and push test, I get the following message: "Failed to construct test pipeline for 'OSS - Open Sound System'"(or the alsa equivalent).

However, when I select alsa or oss and close gstreamer-properties, I have system sounds, which is nice. 

Unfortunately, if I try to play anything on rhythmbox, I get a new message: 
"ALSA device "default" is already in use by another program"
or
"OSS device "/dev/dsp" is already in use by another program."

humbug.

the following is an lsmod, I checked the fedora install, and it uses snd_maesdro3, just like this does:
Module                  Size  Used by
radeon                115236  2
acpi                    5900  0
proc_intf               3968  0
freq_table              4356  1 acpi
cpufreq_userspace       5336  2
cpufreq_powersave       2048  0
ds                     17796  4
button                  6936  0
ac                      5132  0
battery                 9740  0
ipv6                  230020  8
af_packet              20872  2
eepro100               28300  0
e100                   30208  0
mii                     4864  2 eepro100,e100
ohci1394               32004  0
snd_maestro3           22824  5
yenta_socket           19328  1
pcmcia_core            63156  2 ds,yenta_socket
snd_intel8x0m          18632  5
snd_ac97_codec         59268  2 snd_maestro3,snd_intel8x0m
snd_pcm_oss            48168  0
snd_mixer_oss          16640  7 snd_pcm_oss
snd_pcm                85540  3 snd_maestro3,snd_intel8x0m,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd                    50660  15 snd_maestro3,snd_intel8x0m,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  7 snd
snd_page_alloc         11144  2 snd_intel8x0m,snd_pcm
hw_random               5652  0
usblp                  12032  0
uhci_hcd               29328  0
usbcore               104292  4 usblp,uhci_hcd
shpchp                 87276  0
pciehp                 83948  0
pci_hotplug            30640  2 shpchp,pciehp
intel_agp              20512  1
agpgart                31784  2 intel_agp
floppy                 54996  0
pcspkr                  3816  0
rtc                    12216  0
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
sbp2                   22408  0
ieee1394              100536  2 ohci1394,sbp2
joydev                  9536  0
ide_cd                 38276  0
tsdev                   7168  0
mousedev               10124  1
evdev                   9088  1
psmouse                17800  0
sr_mod                 15780  0
scsi_mod              115148  2 sbp2,sr_mod
cdrom                  35872  2 ide_cd,sr_mod
ext3                  109544  2
jbd                    54552  1 ext3
ide_generic             1664  0
piix                   12576  1
ide_disk               16768  5
ide_core              125272  4 ide_cd,ide_generic,piix,ide_disk
unix                   25904  852
fan                     4236  0
thermal                13200  0
processor              17712  2 acpi,thermal
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb


Any thoughts? All help would be greatly appreciated.

Thanks

EDIT:
Ok, system sounds now work no matter what I choose in g-streamer properties, but everything else is still the same as above. I didn't change anything, but I did update all my packages.

---

### Post by originil on 2005-02-10
Alright, I fixed it!
Bizzarely, it apparently had to do with the internal ac97 modem... I think it was picking it up as a sound card. 

I disabled it in the bios, and am now happy.

Now, perhaps there's a way to fix the autodetect... doesn't matter, though, since I never use the modem.

Money.

---

