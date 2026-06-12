---
title: "DVD Writer Problem"
date: 2005-04-13
forum: Hardware &amp; Laptops
---

### Post by Nez7165 on 2005-04-13
My dvd writer dose not work at the moment and have no idea wat to do and how to sort it. It pickes it up and it can write cds but i cant get it to write dvd's at all. It always says that it cant write cd >= 100 mins. Also i think that it is only using cdrw drivers and not nowing it is a dvd writer if that makes sence please please help THANKS NEIL!!

---

### Post by Nez7165 on 2005-04-13
Sorry forgot to add that i use dvdrecord and dose not work and k3b dos not pick it up properly eaither.

---

### Post by Cmdr_K00n on 2005-04-13
DUUDE!

Post the output of the folowingg commands here

<code>dmesg | grep hdX</code> where X is (a,b,c) ie for the device

<code>lsmod</code>

Also, what program are you using? Have you tried Graveman? I also installed K3B using instructions on the forums.

---

### Post by Nez7165 on 2005-04-13
neil@NeilsPc:~$ dmesg | grep hdc
    ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:pio
hdc: LITE-ON DVDRW LDW-851S, ATAPI CD/DVD-ROM drive
hdc: ATAPI 40X DVD-ROM CD-R/RW drive, 2048kB Cache
hdc: rw=0, want=68, limit=4
hdc: rw=0, want=1252, limit=4
hdc: rw=0, want=1028, limit=4
hdc: rw=0, want=68, limit=4
isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
neil@NeilsPc:~$

---

### Post by Nez7165 on 2005-04-13
neil@NeilsPc:~$ lsmod
Module                  Size  Used by
nls_cp437               5888  0
isofs                  33720  0
udf                    77060  0
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
ipv6                  229504  13
sata_sil                8068  0
libata                 44548  1 sata_sil
ohci1394               31876  0
e1000                  77748  0
snd_intel8x0           29984  4
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
i2c_i801                8076  0
i2c_core               21264  1 i2c_i801
ehci_hcd               29444  0
uhci_hcd               30224  0
usbcore               107384  3 ehci_hcd,uhci_hcd
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
intel_mch_agp          10000  0
intel_agp              20636  1
agpgart                31784  2 intel_mch_agp,intel_agp
analog                 10784  0
gameport                4608  1 analog
floppy                 54864  0
pcspkr                  3816  0
rtc                    12216  0
md                     43856  0
evdev                   9088  0
dm_mod                 53116  1
tsdev                   7488  0
capability              5000  0
commoncap               7808  1 capability
sr_mod                 16036  0
sbp2                   22408  0
scsi_mod              119936  3 libata,sr_mod,sbp2
ieee1394              100408  2 ohci1394,sbp2
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
piix                    9988  1
ide_disk               18176  3
ide_core              118988  4 ide_cd,ide_generic,piix,ide_disk
unix                   26164  930
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

---

### Post by Cmdr_K00n on 2005-04-13
1:) Did it ever work before?
2:) What programs you using?

I had a look on the net and I ran up against some bad reviews of it

---

### Post by Nez7165 on 2005-04-13
wat u mean im alittle confused about wat got bad reviews. and i was using dvdrecord and i tryed k3b. It has not worked but i have only changed to linux recently and am now having this problem. it worked fine in windows.

---

### Post by Cmdr_K00n on 2005-04-13
Ok good, so at least it is NOT the drive.

Firstly, you are using Ubuntu, or Kubuntu?
Secondly, how did you install K3b?
[http://www.ubuntulinux.org/wiki/K3BHowto](http://www.ubuntulinux.org/wiki/K3BHowto)
This is a link on the proper way to do it, cause it can fux0r stuff up apparently.
Thirdly, try to install
```
apt-get install graveman
``` 

See if this works

---

### Post by Nez7165 on 2005-04-13
using Ubuntu hoary 5.04 and installed it from the deb file i got of the snaptic installer. and not the drive is working fine. will try that program now

---

### Post by Nez7165 on 2005-04-13
installed that program wat do i do now i have run it is there anything inperticulare u want me 2 do in it??

---

### Post by Cmdr_K00n on 2005-04-13
How about you tell me if it picks up your burner, and try to burn a dvd in it!

Applications -> accessories ->Graveman

---

### Post by Cmdr_K00n on 2005-04-13
Also, in k3b goto

Settings-> Configure K3b -> Devices, 

And tell me what is says in the fields marked  "Burns DVD's"

If it says there that it doesnt, then it could be a problem.
Othewise, are you susre you selected
 "NEW DATA DVD PROJECT" from the bottom part of the screen?

Because you may have accidently selected a cd project layout, which will not let you burn >100 seconds or whatever

---

### Post by Nez7165 on 2005-04-13
K3B says

Writes dvd-r(w) = yes

Writes dvd+r(w) = yes


the dule layers are no.

Hope that helps

---

### Post by Nez7165 on 2005-04-13
in gravesman
i choose a data dvd and put in a files and all i can do is write to a iso. but ubuntu picks up that i put in a blank dvd.

---

### Post by Cmdr_K00n on 2005-04-13
Well im spent on this one, sorry I could not be of more help!

---

