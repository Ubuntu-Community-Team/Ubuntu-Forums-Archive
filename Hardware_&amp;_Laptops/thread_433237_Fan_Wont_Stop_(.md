---
title: "Fan Wont Stop :("
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by cellfish on 2007-05-04
Hello everyone,

im using a Toshiba Equium laptop and currently running Ubuntu 7.04, Feisty Fawn. My fan wont stop, its like im running to many things when im just on google or using amsn. Its so fustrating and enoying it makes so much noise. Ive tried everything, some other people have also been having this problem and posted reports apparently its a bug? If there is a solution to this problem i would be really greatfull if anyone could help me out. I dont have this problem when im using XP.

i have got rid of powernowd but nothings changed.

some helpful information below. Thanks in advanced for any help

uname -a
> 
Linux cellfish-laptop 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

lsmod
> 
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
radeon                124576  3 
drm                    81044  4 radeon
dev_acpi               12292  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
asus_acpi              17308  0 
video                  16388  0 
battery                10756  0 
sbs                    15652  0 
ac                      6020  0 
dock                   10268  0 
button                  8720  0 
backlight               7040  1 asus_acpi
container               5248  0 
i2c_ec                  5888  1 sbs
ipv6                  268704  10 
cpufreq_ondemand        9228  0 
freq_table              5792  1 cpufreq_ondemand
sbp2                   23812  0 
lp                     12452  0 
fuse                   46612  0 
snd_atiixp_modem       17160  0 
snd_atiixp             20620  1 
snd_ac97_codec         98336  2 snd_atiixp_modem,snd_atiixp
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
pcmcia                 39212  0 
ac97_bus                3200  1 snd_ac97_codec
snd_pcm                79876  4 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
joydev                 10816  0 
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
wlan_scan_sta          14976  1 
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ath_rate_sample        14080  1 
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath_pci                97312  0 
i2c_piix4               9740  0 
psmouse                38920  0 
wlan                  204484  4 wlan_scan_sta,ath_rate_sample,ath_pci
irda                  201276  0 
serio_raw               7940  0 
i2c_core               22784  2 i2c_ec,i2c_piix4
ati_agp                10124  1 
agpgart                35400  2 drm,ati_agp
pcspkr                  4224  0 
crc_ccitt               3072  1 irda
shpchp                 34324  0 
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
snd                    54020  13 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath_hal               192592  3 ath_rate_sample,ath_pci
soundcore               8672  1 snd
snd_page_alloc         10888  3 snd_atiixp_modem,snd_atiixp,snd_pcm
pci_hotplug            32576  1 shpchp
af_packet              23816  8 
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_disk               17024  3 
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
8139too                27648  0 
atiixp                  7440  0 [permanent]
generic                 5124  0 [permanent]
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
ata_generic             9092  0 
ehci_hcd               34188  0 
libata                125720  1 ata_generic
scsi_mod              142348  2 sbp2,libata
ohci_hcd               22532  0 
usbcore               134280  3 ehci_hcd,ohci_hcd
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

> 
cellfish@cellfish-laptop:~$  cat /proc/acpi/processor/CPU0/throttling
<not supported>


---

### Post by hyde on 2007-05-11
I have same problem, running Ubuntu 7.04 on Asus A2500D laptop.
Powernowd is required due to AMD processor. It works nicely first, but sometimes fan starts and then it never stops until reboot. Really annoying because the fan on my laptop is very noisy.

This issue came with Ubuntu 6.04 first time (this laptop has this very same issue on XP also!). 
I think that this is kernel related issue?
I've tried latest PCLOS, and I did not find this fan problem then. 

Any hints for this? I've been away from Ubuntu a while, but decided to install this 7.04. 
Looking good, but this fan problem could be a major no-go for this distro.

---

### Post by Xeor on 2007-05-11
I had the same problem on my laptop:

I opened it and used air spray to blow the dust out of the fan/radiator.

---

### Post by k1001001 on 2007-05-11
Same here. I have an Averatec laptop with an AMD processor. This thing is loud as crap.

---

### Post by Visham on 2007-05-19
Same problem with A6Km. Be it XP, server 2003, or Kubuntu... Anyone know how to fix this? Is it related to the bios?

---

### Post by Koant on 2007-06-07
Same here, on my Toshiba TECRA. I've just upgraded from Dapper Drake to Feisty Fawn and since then the fan seems to go off very often. 
'top' never reveals any greedy process so I don't think it's due to anything I'm running. Besides, I'm running exactly the same apps as before the upgrade and didn't have this problem.
If someone has any idea, please share! thanks.

---

### Post by masmre on 2007-11-25
> **Visham said:**
> Same problem with A6Km. Be it XP, server 2003, or Kubuntu... Anyone know how to fix this? Is it related to the bios?

What bios you have? I have same a6km MB, and only old (2005) 202as  bios working normal.  
This initial BIOS release (202AS) works without USB problems to.

---

### Post by Yellow Pasque on 2007-11-25
You may want to try installing the lm-sensors package and using the pwmconfig script.
Off the top of my head IIRC:
```
sudo apt-get install lm-sensors
sudo sensors-detect
sudo pwmconfig
```

Answer yes to the questions about probing buses that sensors-detect asks you.

EDIT: Not all mobos are capable of PWM (Pulse Width Modulation). For reference, PWM works by turning the 12V signal to the fan on and off at a given rate (thus creating square pulses when you look at Voltage vs. time). Higher PWM values = a longer pulse = fan runs faster

---

