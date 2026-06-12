---
title: "irda on asus w1n"
date: 2006-03-01
forum: Hardware &amp; Laptops
---

### Post by nemesis333 on 2006-03-01
hi,
i have ubuntu 5.10 running, and i want to get my irda interface on my asus w1978nalp running.
i have installed:
      * lirc-0.7.0.1-1ubuntu3
      * lirc-modules-source-0.7.0.1-1ubuntu3
      * lirc-x-0.7.0.1-1ubuntu3

lspci says:
```
root@Nemesis-Mobil:/dev# lspci
0000:00:00.0 Host bridge: Intel Corp. 82855PM Processor to I/O
Controller (rev 21)
0000:00:01.0 PCI bridge: Intel Corp. 82855PM Processor to AGP Controller
(rev 21)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM
(ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM
(ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM
(ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB
2.0 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller
(rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA
Storage Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M)
SMBus Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM
(ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M)
AC'97 Modem Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350
[Mobility Radeon 9600 M10]
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd. Yukon
Gigabit Ethernet 10/100/1000Base-T Adapter (rev 13)
0000:02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
0000:02:01.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
0000:02:01.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394
Controller (rev 04)
0000:02:02.0 Multimedia controller: Philips Semiconductors SAA7133 Audio +video broadcast decoder (rev f0)
0000:02:03.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
```

lsmod says:
```
lsmod:
root@Nemesis-Mobil:/dev# lsmod
Module                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_centrino      7380  1
cpufreq_userspace       4444  1
cpufreq_stats           5124  0
freq_table              4484  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
pcmcia                 24584  4
lirc_dev               13540  0
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
asus_acpi              12564  0
ipv6                  217408  8
irtty_sir               7808  0
sir_dev                17324  1 irtty_sir
irda                  159804  2 irtty_sir,sir_dev
crc_ccitt               2176  1 irda
pcspkr                  3652  0
rtc                    11832  0
ipw2200                92680  0
firmware_class          9472  1 ipw2200
ieee80211              27012  1 ipw2200
ieee80211_crypt         5636  2 ipw2200,ieee80211
saa7134                98772  0
video_buf              19844  1 saa7134
v4l2_common             5888  1 saa7134
v4l1_compat            12420  1 saa7134
i2c_core               19728  2 i2c_acpi_ec,saa7134
ir_common               7428  1 saa7134
videodev                9344  1 saa7134
ohci1394               30644  0
yenta_socket           22540  2
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_intel8x0           30144  2
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  3 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  6
snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  4 saa7134,snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
tpm_atmel               5504  0
tpm_nsc                 6528  0
tpm                     9504  2 tpm_atmel,tpm_nsc
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
intel_agp              21276  1
agpgart                32328  1 intel_agp
nls_iso8859_1           4224  1
nls_cp437               5888  1
vfat                   12288  1
fat                    46492  1 vfat
dm_mod                 50364  1
joydev                  9280  0
tsdev                   7616  0
evdev                   9088  1
sr_mod                 15652  0
sbp2                   21128  0
scsi_mod              124872  2 sr_mod,sbp2
ieee1394               90936  2 ohci1394,sbp2
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  0
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  2 speedstep_centrino,thermal
fan                     4740  0
usbhid                 30688  0
skge                   33040  0
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104316  4 usbhid,ehci_hcd,uhci_hcd
ide_cd                 36996  0
cdrom                  33952  2 sr_mod,ide_cd
ide_disk               16128  4
ide_generic             1664  0
piix                    9476  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,piix
unix                   24624  416
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
```

if i want to run mode2:
```
root@Nemesis-Mobil:/dev# mode2
mode2: error opening /dev/lirc
mode2: No such file or directory
```

modrobe lirc_sir says:
```
root@Nemesis-Mobil:/dev# modprobe lirc_sir
FATAL: Error inserting lirc_sir
(/lib/modules/2.6.12-10-386/misc/lirc_sir.ko): Device or resource busy

```

from windows i have following settings:
```
      * ACPI\PNP0510\2
      * max. Verbindungsrate 115200
      * DMA3
      * E/A 02F8-02FF
      * IRQ3
```

you see, it wont work, and i don't know why :( 

i hope somebody her can help me to get my irda-device working.

p.s.: sry for my bad english, i'm from germany and my english is not the best at the moment :rolleyes: 
i hope somebody will nervertheless help me :) 

thx

---

