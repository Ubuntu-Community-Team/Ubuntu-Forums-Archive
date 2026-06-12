---
title: "xorg crashes when I try to use opengl"
date: 2005-03-12
forum: Hardware &amp; Laptops
---

### Post by fackamato on 2005-03-12
Hi

I'm using Ubuntu Hoary with xorg, some info below:

[size=1]```
Linux fackamato 2.6.10-4-686-smp #1 SMP Sat Mar 12 11:15:47 GMT 2005 i686 GNU/Linux

Module                  Size  Used by
proc_intf               4260  0
cpufreq_powersave       1856  0
cpufreq_userspace       6240  0
cpufreq_ondemand        6728  0
freq_table              4320  0
video                  16196  0
battery                10212  0
container               4544  0
button                  6704  0
pcc_acpi               11232  0
sony_acpi               6152  0
ac                      4900  0
nls_cp437               5824  1
isofs                  36700  1
ipv6                  257696  14
nfs                   208964  3
lockd                  64872  2 nfs
sunrpc                148996  6 nfs,lockd
snd_ens1371            24448  3
snd_rawmidi            25024  1 snd_ens1371
snd_seq_device          8716  1 snd_rawmidi
snd_ac97_codec         74336  1 snd_ens1371
snd_pcm_oss            52836  0
snd_mixer_oss          19968  2 snd_pcm_oss
snd_pcm                95780  4 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              25572  2 snd_pcm
snd                    56580  10 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc          9988  1 snd_pcm
gameport                4864  1 snd_ens1371
tuner                  22020  0
saa7134               103240  0
video_buf              21956  1 saa7134
v4l2_common             5888  1 saa7134
v4l1_compat            14468  1 saa7134
soundcore              10400  3 snd,saa7134
ir_common               5028  1 saa7134
videodev               10080  1 saa7134
joydev                  9920  0
e1000                  86708  0
tsdev                   7776  0
ata_piix                9412  4
libata                 49476  1 ata_piix
ehci_hcd               33220  0
usbhid                 32384  0
uhci_hcd               33488  0
usbcore               119480  4 ehci_hcd,usbhid,uhci_hcd
shpchp                 99620  0
pci_hotplug            33980  1 shpchp
intel_agp              22332  0
intel_mch_agp          10512  1
floppy                 59472  0
pcspkr                  3788  0
rtc                    12776  0
nls_iso8859_1           4160  1
ntfs                  111408  1
evdev                   9600  0
md                     47920  0
dm_mod                 60480  1
capability              4872  0
commoncap               8032  1 capability
loop                   16840  2
nvidia               3923388  8
agpgart                34284  3 intel_agp,intel_mch_agp,nvidia
w83781d                34056  0
eeprom                  7576  0
i2c_sensor              3712  2 w83781d,eeprom
i2c_isa                 2144  0
i2c_i801                8652  0
i2c_core               22720  7 tuner,saa7134,w83781d,eeprom,i2c_sensor,i2c_isa,i2c_i801
parport_pc             37924  1
lp                     11464  0
parport                37352  2 parport_pc,lp
ide_cd                 42052  0
cdrom                  40476  1 ide_cd
mousedev               11612  1
psmouse                21736  0
sd_mod                 18080  5
scsi_mod              128320  2 libata,sd_mod
reiserfs              264400  1
ext2                   67816  0
ext3                  137832  4
jbd                    63416  1 ext3
mbcache                 8452  2 ext2,ext3
ide_generic             1536  0
ide_disk               20896  4
piix                   10884  1
ide_core              129656  4 ide_cd,ide_generic,ide_disk,piix
unix                   28692  736
thermal                13672  0
processor              23400  1 thermal
fan                     4612  0
fbcon                  37856  71
font                    8416  1 fbcon
bitblit                 5696  1 fbcon
vesafb                  6948  1
cfbcopyarea             4032  1 vesafb
cfbimgblt               3136  1 vesafb
cfbfillrect             3712  1 vesafb

0000:00:00.0 Host bridge: Intel Corp. 82875P Memory Controller Hub (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 82875P Processor to AGP Controller (rev 02)
0000:00:03.0 PCI bridge: Intel Corp. 82875P Processor to PCI to CSA Bridge (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corp. 82801EB/ER (ICH5/ICH5R) LPC Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801EB/ER (ICH5/ICH5R) Ultra ATA 100 Storage Controller (rev 02)
0000:00:1f.2 IDE interface: Intel Corp. 82801EB (ICH5) Serial ATA 150 Storage Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3 Ti 200] (rev a3)
0000:02:01.0 Ethernet controller: Intel Corp. 82547EI Gigabit Ethernet Controller (LOM)
0000:03:03.0 Multimedia controller: Philips Semiconductors SAA7134 (rev 01)
0000:03:05.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
```[/size]

I'm using the nVidia driver: [size=1]> Version: 1.0-7167
Operating System: Linux IA32
Release Date: March 11, 2005[/size]

I open up a terminal, type glxgears, press enter and X immediatly crashes. GDM restarts it of course...

Any idea on why this happens? :<

Going to crash my X now, to get a logfile, hang on.

**Another crash later:** See the logs at [http://www.tehjunkyard.net/Xorg.0.log.old2.txt](http://www.tehjunkyard.net/Xorg.0.log.old2.txt) and [http://www.tehjunkyard.net/Xorg.0.log2.txt](http://www.tehjunkyard.net/Xorg.0.log2.txt) .

---

### Post by alastair on 2005-03-12
So, what's in the NVidia driver section in the xorg.conf?

You have an error reported in your log :

(EE) NVIDIA(0): Failed to load GLX

So ... the output of "glxinfo" probably shows nothing, or cause problems.

Read the NVidia README file and look to see what problems exist. Perhaps take out some of the more "advanced" options e.g. render accel, or composite etc.

Read or ask on NVidia forums. Perhaps downgrade the driver.

---

### Post by fackamato on 2005-03-12
[QUOTE=alastair]So, what's in the NVidia driver section in the xorg.conf?

You have an error reported in your log :

(EE) NVIDIA(0): Failed to load GLX

So ... the output of "glxinfo" probably shows nothing, or cause problems.

Read the NVidia README file and look to see what problems exist. Perhaps take out some of the more "advanced" options e.g. render accel, or composite etc.

Read or ask on NVidia forums. Perhaps downgrade the driver.[/QUOTE]

Hm, well downgrading the driver to 66.whatitwhas solved the issue. Everything works... so it must be a problem with the new driver. Damnit, I wanted to see more fps ;). I'll do some searching.

Thanks.

---

### Post by fackamato on 2005-03-12
Problem solved! A bit of searching on the nVidia forums revealed that I needed to patch the driver.

[http://www.nvnews.net/vbulletin/showthread.php?t=47405](http://www.nvnews.net/vbulletin/showthread.php?t=47405)
[http://www.nvnews.net/vbulletin/showthread.php?t=47489](http://www.nvnews.net/vbulletin/showthread.php?t=47489)

There is also a patch which improves 2D/3D performance when using agpgart, I'm trying that one now.

**Edit:** Applying the performance improving patch degraded my performance, I got 1900fps in glxgears with the patch and 2280fps without it. ;o

(i875 northbridge, GeForce 3 Ti200 using agpgart.)

---

