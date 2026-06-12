---
title: "Hard Drive Light Problem"
date: 2007-06-24
forum: Hardware &amp; Laptops
---

### Post by YourFriendlyGopher on 2007-06-24
Hi all,

The hard drive light on my PC is always on but still flashes more brightly when it is being accessed. While it's not a major problem, I'd still like to fix it. I'm thinking it has something to do with Kubuntu (6.10) since it doesn't do this in Windows, and on rare occasions doesn't do it in Kubuntu. I'm not sure what kind of output you'd want for this so I'll have a stab at it and give you lspci and lsmod:

lspci:

```

00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev
a2)
00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audi
o Controller (rev a1)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (r
ev a2)
00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev
 a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev
 a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTra
nsport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address
Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Con
troller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscella
neous Control
01:00.0 VGA compatible controller: ATI Technologies Inc R480 [Radeon X850Pro]
01:00.1 Display controller: ATI Technologies Inc R480 [Radeon X850Pro] (Secondar
y)

```

lsmod:

```

Module                  Size  Used by
rfcomm                 42260  0
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
ipv6                  272288  12
fglrx                 406988  44
powernow_k8            15008  0
cpufreq_userspace       5408  0
cpufreq_stats           7744  0
freq_table              6048  2 powernow_k8,cpufreq_stats
cpufreq_powersave       2944  0
cpufreq_ondemand        8876  1
cpufreq_conservative     8712  0
video                  17540  0
tc1100_wmi              8324  0
sony_acpi               6412  0
sbs                    16804  0
pcc_acpi               14080  0
i2c_ec                  6272  1 sbs
hotkey                 11556  0
dev_acpi               12292  0
container               5632  0
button                  7952  0
battery                11652  0
asus_acpi              17688  0
ac                      6788  0
af_packet              24584  0
fuse                   43912  2
lp                     12964  0
sg                     37404  0
psmouse                41352  0
snd_intel8x0           34844  4
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
tsdev                   9152  0
serio_raw               8452  0
snd_pcm_oss            47360  0
snd_mixer_oss          19584  1 snd_pcm_oss
parport_pc             37796  1
parport                39496  2 lp,parport_pc
evdev                  11392  1
pcspkr                  4352  0
snd_pcm                84612  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  2 snd_pcm
floppy                 63044  0
i2c_nforce2             8192  0
i2c_core               23424  2 i2c_ec,i2c_nforce2
amd64_agp              13124  1
agpgart                34888  2 fglrx,amd64_agp
snd                    58372  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
shpchp                 42144  0
pci_hotplug            32828  1 shpchp
ext3                  142728  4
jbd                    62228  1 ext3
usbhid                 45152  0
ehci_hcd               34696  0
forcedeth              32268  0
ohci_hcd               22532  0
usbcore               134912  4 usbhid,ehci_hcd,ohci_hcd
ide_generic             2432  0
ide_cd                 33696  0
cdrom                  38944  1 ide_cd
generic                 5764  0
sd_mod                 22656  8
amd74xx                15260  0 [permanent]
sata_nv                11268  6
libata                 74892  1 sata_nv
scsi_mod              144648  3 sg,sd_mod,libata
thermal                15624  1
processor              31560  2 powernow_k8,thermal
fan                     6020  1
fbcon                  41504  0
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0
capability              5896  0
commoncap               8704  1 capability

```

Thanks for any help!

---

### Post by YourFriendlyGopher on 2007-06-24
Bee you em pee.

---

### Post by FredSambo on 2007-06-28
I have the same issue, it just started.  I am running Ubuntu Feisty.  :(

---

### Post by speaker219 on 2007-06-28
What model computer do you have?

---

### Post by FredSambo on 2007-06-28
I just realized this is the laptop forum.  Oops.

I have a Sony Viao PCV-2232 It is a desktop computer.  This problem just started, I think it may have something to do with my crappy DVD drive.  Not sure though.

---

### Post by FredSambo on 2007-06-28
Yep. it was my crappy DVD drive.  I took it out and the problem is solved!

---

