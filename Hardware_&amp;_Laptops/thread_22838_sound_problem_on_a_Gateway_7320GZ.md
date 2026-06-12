---
title: "sound problem on a Gateway 7320GZ"
date: 2005-03-29
forum: Hardware &amp; Laptops
---

### Post by pinecone on 2005-03-29
first off, I've been using linux for several months, and I've fallen in love with it.  I'm still probably somewhat of a newbie, so try and keep any answers yall give me fairly easy.  Thanks in advance :)

Here is a link to the laptop I'm using

[http://www.gateway.com/home/products/ret/ret_7320GZ.shtml](http://www.gateway.com/home/products/ret/ret_7320GZ.shtml)

the sound card in it is 

lsmod gives me: 
```
Module                  Size  Used by
af_packet              20872  2
nls_cp437               6016  1
isofs                  33976  1
udf                    79876  0
i830                   68644  3
acpi                    5900  0
proc_intf               3968  0
freq_table              4356  1 acpi
cpufreq_userspace       5336  2
cpufreq_powersave       2048  0
button                  6936  0
ac                      5132  0
battery                 9740  0
ipv6                  230020  8
ds                     17796  2
b44                    19972  0
mii                     4864  1 b44
yenta_socket           19328  0
pcmcia_core            63156  2 ds,yenta_socket
ohci1394               32004  0
snd_intel8x0m          18632  2
snd_intel8x0           33068  3
snd_ac97_codec         59268  2 snd_intel8x0m,snd_intel8x0
snd_pcm_oss            48168  0
snd_mixer_oss          16640  4 snd_pcm_oss
snd_pcm                85540  3 snd_intel8x0m,snd_intel8x0,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd_page_alloc         11144  3 snd_intel8x0m,snd_intel8x0,snd_pcm
gameport                4736  1 snd_intel8x0
snd_mpu401_uart         7296  1 snd_intel8x0
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  1 snd_rawmidi
snd                    50660  14 snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  4 snd
shpchp                 87276  0
pciehp                 83948  0
pci_hotplug            30640  2 shpchp,pciehp
ehci_hcd               27780  0
uhci_hcd               29328  0
usbcore               104292  4 ehci_hcd,uhci_hcd
intel_agp              20512  1
agpgart                31784  4 intel_agp
pcspkr                  3816  0
rtc                    12216  0
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
parport_pc             32064  0
lp                     10436  0
parport                37320  2 parport_pc,lp
sbp2                   22408  0
ieee1394              100536  2 ohci1394,sbp2
tsdev                   7168  0
joydev                  9536  0
evdev                   9088  1
ide_cd                 38276  1
mousedev               10124  1
psmouse                17800  0
sr_mod                 15780  0
scsi_mod              115148  2 sbp2,sr_mod
cdrom                  35872  2 ide_cd,sr_mod
ext3                  109544  1
jbd                    54552  1 ext3
ide_generic             1664  0
piix                   12576  1
ide_disk               16768  3
ide_core              125272  4 ide_cd,ide_generic,piix,ide_disk
unix                   25904  808
fan                     4236  0
thermal                13200  0
processor              17712  2 acpi,thermal
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb

```

on the mixer (not alsa, the one that appears next to the clock)  I have four tabs: Conexant id 30 [OSS MIXER], Conexant id 30 [OSS MIXER] (again), Intel 82801DB-ICH4 [Alsa Mixer], Intel 82801DB-ICH4 Modem [Alsa Mixer]

The second Conexant tab has nothing at all on it, neither does the second Intel tab.

The drive in windows is made by conexant.  That's all the info I can think of to give yall.  thanks in advance for your help


ps yes, I've umuted and turned up all the mixers :)

---

### Post by pinecone on 2005-04-02
is there any more information I need to give yall?

---

### Post by pinecone on 2005-04-04
[QUOTE=pinecone]is there any more information I need to give yall?[/QUOTE]
 The problem was solved for me by upgrading to hoary, updating it, and then muting External under alsa mixer, incase anyone else has been having this problem.  On a side note, can someone tell me how to make External muted by default when I start up?  It's not really important, but it'd be more convenient.

---

