---
title: "tv card, no sound with ubuntu breezy badger"
date: 2006-04-30
forum: Hardware &amp; Laptops
---

### Post by esiotrot on 2006-04-30
help
I have a pinnacle pctvpro card and I am unable to get any audio. If I plug my speakers directly into the card, or if I link to the microphone input, all I get is a hissing noise. I cannot see anything indicating a problem in dmsg or messages. The picture is OK.
thanx

---

### Post by Mustard on 2006-04-30
Try the lsmod command to see what output you get and paste it in here.  From that you could at least see if its loading modules for sound.  Is it a pci card?  Try lspci too, if so.

---

### Post by esiotrot on 2006-05-01
Module                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
radeon                 68352  1
drm                    58004  2 radeon
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  6
af_packet              20232  2
pcspkr                  3652  0
rtc                    11832  0
floppy                 52692  0
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44688  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            25792  1
gameport               14472  1 snd_via82xx
snd_ac97_codec         72188  1 snd_via82xx
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  2 snd_seq,snd_pcm
snd_page_alloc         10120  2 snd_via82xx,snd_pcm
snd_mpu401_uart         6784  1 snd_via82xx
snd_rawmidi            22816  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    48644  13 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9184  1 snd
i2c_viapro              7696  0
ohci1394               30644  0
bt878                   9912  0
tuner                  24488  0
tda9887                13208  0
bttv                  141456  1 bt878
video_buf              19844  1 bttv
firmware_class          9472  1 bttv
i2c_algo_bit            8584  1 bttv
v4l2_common             5888  1 bttv
btcx_risc               4872  1 bttv
tveeprom               12568  1 bttv
i2c_core               19728  7 i2c_acpi_ec,i2c_viapro,tuner,tda9887,bttv,i2c_algo_bit,tveeprom
videodev                9344  1 bttv
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
amd64_agp              11464  1
agpgart                32328  2 drm,amd64_agp
dm_mod                 50364  1
tsdev                   7616  0
evdev                   9088  0
sr_mod                 15652  0
sbp2                   21128  0
ieee1394               90936  2 ohci1394,sbp2
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
sd_mod                 17424  1
usb_storage            64704  0
via_rhine              20356  0
mii                     5248  1 via_rhine
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104316  4 usb_storage,ehci_hcd,uhci_hcd
sata_via                8836  5
libata                 47876  1 sata_via
scsi_mod              124872  5 sr_mod,sbp2,sd_mod,usb_storage,libata
ide_cd                 36996  0
cdrom                  33952  2 sr_mod,ide_cd
ide_disk               16128  3
ide_generic             1664  0
via82cxxx              12188  1
ide_core              125268  5 usb_storage,ide_cd,ide_disk,ide_generic,via82cxxx
unix                   24624  793
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon
r


 lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc.: Unknown device 0204
0000:00:00.1 Host bridge: VIA Technologies, Inc.: Unknown device 1204
0000:00:00.2 Host bridge: VIA Technologies, Inc.: Unknown device 2204
0000:00:00.3 Host bridge: VIA Technologies, Inc.: Unknown device 3204
0000:00:00.4 Host bridge: VIA Technologies, Inc.: Unknown device 4204
0000:00:00.7 Host bridge: VIA Technologies, Inc.: Unknown device 7204
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800 South]0000:00:06.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
0000:00:07.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:00:07.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0000:00:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [K8T800 South]0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 5940 (rev 01)

---

### Post by Mustard on 2006-05-02
Well it looks like its recognising the device and loading modules for it.  Does the card need to be connected to a sound card of some kind normally?

Mine is an old one, that has a connection from the line out on the TV Card to the line in on my soundcard.

---

### Post by esiotrot on 2006-05-02
[QUOTE=Mustard]Well it looks like its recognising the device and loading modules for it.  Does the card need to be connected to a sound card of some kind normally?

Mine is an old one, that has a connection from the line out on the TV Card to the line in on my soundcard.[/QUOTE]

I have tried both direct to my speakers and connecting to my sound card with the same result. I suppose the card could be faulty but I dont know how to prove this??

thanx

---

### Post by Mustard on 2006-05-02
Which volume controls are you using for the TV card?

---

### Post by futz on 2006-05-02
This may not be the cure, but if your TV card has the same chipset as the one in my Fedora box, it may well be. I had the exact same problem - just static hiss instead of sound.

This thread over at linuxquestions.org had the cure for me.
[http://www.linuxquestions.org/questions/showthread.php?t=272105](http://www.linuxquestions.org/questions/showthread.php?t=272105)
You'll see my post at the bottom.

---

### Post by esiotrot on 2006-05-06
hi mustard
I have tried both the alsa and oss mixers with the same result.

I have looked at the link suggested by futz and this looks promising except that my system (ubuntu breezy) does not have a modprobe.conf file (or I cant find it).????

---

### Post by futz on 2006-05-06
[QUOTE=esiotrot]I have looked at the link suggested by futz and this looks promising except that my system (ubuntu breezy) does not have a modprobe.conf file (or I cant find it).????[/QUOTE]
I've done a little digging and have something that ***may*** help. I have no way of testing it without stringing cable to this box and moving my TV card over. And that aint gonna happen! :cool: 

[http://www.ubuntuforums.org/archive/index.php/t-1994.html](http://www.ubuntuforums.org/archive/index.php/t-1994.html)
In this thread I found this info:
> all the files inside /etc/modprobe.d comprise modprobe.conf. Stick it in any one you want, then run update-modules.
and this
> Debian still uses /etc/modules/ to house all module configurations. There's where all the config goes. If it's a module-init-tools specific command (like load or unload actions), they need to go in /etc/modprobe.d/. After editing, you must run update-modules for your changes to be merged with the system modules config.

After looking at the files in /etc/modprobe.d, I would guess you'd put that option in alsa-base. I know nothing about all this, but it looks like a likely place. And it's unlikely to break anything if it doesn't help.

---

### Post by esiotrot on 2006-05-07
hi 
this looked promising but it is just the same. I think I need to prove my hardware so I will try to borrow a known working card 
thanx

---

