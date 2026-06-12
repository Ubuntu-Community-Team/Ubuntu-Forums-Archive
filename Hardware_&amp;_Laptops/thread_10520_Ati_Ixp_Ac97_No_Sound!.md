---
title: "Ati Ixp Ac97 No Sound?!"
date: 2005-01-08
forum: Hardware &amp; Laptops
---

### Post by telmo on 2005-01-08
I just can't get any sound out of my soundcard!!! I'm going crazy!
I tried everything i saw in simillar posts, but my soundcard is still not recognized.

I tried Hoary, and it works partially. Why can't i just get it to work in Warty??? WHY???  :-& 

Is there any solution to this?

I would like to look at Ubuntu as my favourite distro, but not without sound!

PLEASE don't make go back to Fedora... please!

My computer is a HP Pavilion ZX5051EA laptop and here is my lsmod...:

Module                            Size  Used by
acpi                                 5996  0
proc_intf                          3776  0
cpufreq_powersave         1728  0
cpufreq_userspace         5240  2
freq_table                       4196  1 acpi
ipv6                            257028  8
ds                                 18436  4
button                            6584  0
ac                                   4812  0
battery                           9388  0
af_packet                     22088  2
ndiswrapper                 98096  0
ehci_hcd                       30756  0
yenta_socket                20992  0
pcmcia_core                 68404  2 ds,yenta_socket
8139cp                         20256  0
8139too                        25568  0
mii                                   5056  2 8139cp,8139too
crc32                              4288  2 8139cp,8139too
ohci1394                      34884  0
snd_atiixp                     21160  0
snd_ac97_codec           67844  1 snd_atiixp
snd_pcm_oss                52968  0
snd_mixer_oss              19456  1 snd_pcm_oss
snd_pcm                       95140  2 snd_atiixp,snd_pcm_oss
snd_timer                     24900  1 snd_pcm
snd                              55300  6 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore                   10112  1 snd
snd_page_alloc            11432  2 snd_atiixp,snd_pcm
hci_usb                13632  0
bluetooth              48260  1 hci_usb
usblp                  12832  0
joydev                  9728  0
usbhid                 31392  0
usb_storage            66688  0
ohci_hcd               20996  0
usbcore               115684  9 ndiswrapper,ehci_hcd,hci_usb,usblp,usbhid,usb_storage,ohci_hcd
ati_agp                 8460  1
agpgart                33640  1 ati_agp
pcspkr                  3592  0
rtc                    12536  0
md                     48552  0
dm_mod                 57308  1
capability              4520  0
commoncap               7072  1 capability
parport_pc             34752  1
lp                     10724  0
parport                40712  2 parport_pc,lp
sbp2                   23816  0
ieee1394              108408  2 ohci1394,sbp2
ide_cd                 41572  0
evdev                   9440  0
tsdev                   7232  0
mousedev               10220  1
psmouse                19720  0
sr_mod                 16900  0
cdrom                  39392  2 ide_cd,sr_mod
sd_mod                 21344  0
scsi_mod              122508  4 usb_storage,sbp2,sr_mod,sd_mod
reiserfs              240880  1
ext2                   69960  0
ext3                  123880  0
jbd                    60824  1 ext3
mbcache                 9092  2 ext2,ext3
ide_generic             1408  0
ide_disk               18752  3
atiixp                  8696  1
ide_core              136120  5 usb_storage,ide_cd,ide_generic,ide_disk,atiixp
unix                   28304  704
fan                     3980  0
thermal                12976  0
processor              17392  2 acpi,thermal
font                    8352  0
vesafb                  6560  0
cfbcopyarea             3712  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3616  1 vesafb

---

### Post by telmo on 2005-01-09
OK... so i  found the sound works beautifully with the new kernel 2.6.10, but... ndiswrapper stops working! :(

I need them both to work.

Any suggestions?

---

### Post by telmo on 2005-01-16
Solved! Thanks for the help anyway LOL

---

### Post by lsackette on 2005-01-23
I have the same problem.  Could you please post how you solve your sound problem?

Thanks.

---

### Post by telmo on 2005-01-23
[QUOTE=lsackette]I have the same problem.  Could you please post how you solve your sound problem?

Thanks.[/QUOTE]

I just installed the 2.6.10-2.686 Kernel from Hoary repositories.

All you need to do is change the repositories in Synaptic, from Warty to Hoary. ;)

---

