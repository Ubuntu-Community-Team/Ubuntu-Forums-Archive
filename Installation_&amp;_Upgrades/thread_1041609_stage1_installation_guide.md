---
title: "stage1 installation guide?"
date: 2009-01-16
forum: Installation &amp; Upgrades
---

### Post by Meow27 on 2009-01-16
i wanna try doing a stage1 install of kubuntu 8.10

im looking for guides of how to do stage1 installations. (im a newb) but i cant find any

does anyone know any good guides i can use to try doing this?

if possible

---

### Post by logos34 on 2009-01-16
huh?

Do you perhaps mean a [minimal]("https://help.ubuntu.com/community/Installation/MinimalCD") or basic install?

---

### Post by albinootje on 2009-01-16
> **Meow27 said:**
> i wanna try doing a stage1 install of kubuntu 8.10

im looking for guides of how to do stage1 installations. (im a newb) but i cant find any

does anyone know any good guides i can use to try doing this?

Stage1 is an expression used by Gentoo Linux. 
Are you saying that you want to recompile all software from Kubuntu ?

---

### Post by Meow27 on 2009-01-18
i dunno.. i honestly dont know.... i get this graphics glitch every couple of seconds when kubuntu 8.10 is running. i get these box like things that just appear and disappear randomly and its extremely annoying. its probably a foolish thought but i was thinking that compiling it from scratch might remedy the problem.... it probably wont tho >.> :(

---

### Post by albinootje on 2009-01-18
> **Meow27 said:**
> i get these box like things that just appear and disappear randomly and its extremely annoying. 

Can you post the output of the following please :
```

lspci
lsmod

```

You might need another video driver, or tweaking the one you're using.

---

### Post by Meow27 on 2009-01-19
when im on the livecd (for kubuntu 8.10) or when im on hardy as i am now?

but on hardy heres the output

```
meow27@Nebula-Class:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:03.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
06:03.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
06:03.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)

```

```
meow27@Nebula-Class:~$ lsmod
Module                  Size  Used by
isofs                  36388  0 
udf                    88612  0 
ipv6                  267908  8 
i915                   32512  2 
drm                    82452  3 i915
af_packet              23812  2 
binfmt_misc            12808  1 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61028  4 rfcomm,l2cap
vboxnetflt             91400  0 
vboxdrv               117544  1 vboxnetflt
sonypi                 23192  0 
ppdev                  10372  0 
speedstep_centrino      9152  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  1 
cpufreq_conservative     8712  0 
freq_table              5536  3 speedstep_centrino,cpufreq_stats,cpufreq_ondemand
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
tifm_sd                12936  0 
mmc_core               51460  1 tifm_sd
pcmcia                 40876  0 
sony_laptop            35292  0 
snd_hda_intel         346136  4 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
video                  19856  0 
output                  4736  1 video
evdev                  13056  12 
psmouse                40336  0 
snd_seq_dummy           4868  0 
ipw2200               146120  0 
serio_raw               7940  0 
tifm_7xx1               8576  0 
snd_seq_oss            35584  0 
ieee80211              35528  1 ipw2200
ieee80211_crypt         7040  1 ieee80211
tifm_core              11012  2 tifm_sd,tifm_7xx1
snd_seq_midi            9376  0 
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
battery                14212  0 
snd_rawmidi            25760  1 snd_seq_midi
ac                      6916  0 
button                  9232  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
intel_agp              25492  1 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
agpgart                34760  3 drm,intel_agp
pcspkr                  4224  0 
snd                    56996  19 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
soundcore               8800  1 snd
reiserfs              239616  1 
usbhid                 32128  0 
hid                    38784  1 usbhid
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  4 
ata_piix               19588  3 
ata_generic             8324  0 
ohci1394               33584  0 
pata_acpi               8320  0 
e100                   37388  0 
mii                     6400  1 e100
ieee1394               93752  2 sbp2,ohci1394
libata                159600  3 ata_piix,ata_generic,pata_acpi
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146412  4 usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36488  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 

```

---

### Post by albinootje on 2009-01-19
> **Meow27 said:**
> 
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

Thanks.

Can you find out the exact name of your graphics card ?
```

sudo lshw -C display

```

This could be useful to read :
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/284907](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/284907)
[http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_950](http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_950)

---

### Post by Meow27 on 2009-01-19
before reading the links heres the output you wanted

```
meow27@Nebula-Class:~$ sudo lshw -C display
[sudo] password for meow27: 
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0

```

---

