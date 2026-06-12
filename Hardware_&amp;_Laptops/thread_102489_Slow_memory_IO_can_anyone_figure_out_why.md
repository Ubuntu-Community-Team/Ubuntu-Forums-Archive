---
title: "Slow memory IO can anyone figure out why?"
date: 2005-12-12
forum: Hardware &amp; Laptops
---

### Post by Arwyn on 2005-12-12
As topic states my memory IO is incredably slow. By that I mean whenever I do a task that requires a reasonable amount of memory IO (eg open OO.o) my system freezes, the CPU usage shoots up to 100% with 80% of that being IOwait...

Both memory and CPU clock speeds are 333MHz and both are set to such in the BIOS.

The correct modules for my hardware seem to be loaded (lspci and lsmod attached bellow).

Any idea what might be wrong?

lspci:
[INDENT]
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 741/741GX/M741 Host (rev 03)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS]: Unknown device 0003
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
0000:00:09.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 8b)
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX/741/M741/760/M760 PCI/AGP
[/INDENT]

lsmod:
[INDENT]
Module                  Size  Used by
rfcomm                 38748  0
l2cap                  25156  5 rfcomm
bluetooth              48580  4 rfcomm,l2cap
cpufreq_powersave       1792  0
cpufreq_stats           5316  0
cpufreq_userspace       4380  0
cpufreq_ondemand        6108  0
cpufreq_conservative     7012  0
freq_table              4484  1 cpufreq_stats
tc1100_wmi              6788  0
video                  15812  0
battery                 9412  0
container               4480  0
i2c_acpi_ec             5568  0
button                  6544  0
pcc_acpi               11200  0
sony_acpi               5388  0
ac                      4804  0
dev_acpi               11268  0
hotkey                  9380  0
ipv6                  252480  17
af_packet              22088  2
tsdev                   7872  0
snd_mpu401              6408  0
snd_mpu401_uart         7360  1 snd_mpu401
snd_rawmidi            25056  1 snd_mpu401_uart
snd_seq_device          8524  1 snd_rawmidi
analog                 11680  0
gameport               14920  1 analog
irtty_sir               8576  0
sir_dev                18668  1 irtty_sir
irda                  188412  2 irtty_sir,sir_dev
crc_ccitt               2048  1 irda
floppy                 59412  0
pcspkr                  3460  0
rtc                    12408  0
snd_intel8x0           33344  5
snd_ac97_codec         84028  1 snd_intel8x0
snd_pcm_oss            53152  0
snd_mixer_oss          19392  1 snd_pcm_oss
snd_pcm                89032  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24260  2 snd_pcm
snd                    55172  18 snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9696  1 snd
snd_page_alloc         10696  2 snd_intel8x0,snd_pcm
i2c_sis96x              5316  0
i2c_core               21328  2 i2c_acpi_ec,i2c_sis96x
shpchp                 97252  0
pci_hotplug            27636  1 shpchp
sis_agp                 8644  1
agpgart                34888  1 sis_agp
deflate                 4096  0
zlib_deflate           23192  1 deflate
twofish                37568  0
serpent                17280  0
aes_i586               38912  0
blowfish                8064  0
des                    11648  0
sha256                  9472  0
sha1                    2816  0
crypto_null             2368  0
af_key                 33488  0
xfs                   619896  1
exportfs                6016  1 xfs
ext2                   67528  1
mbcache                 9348  1 ext2
dm_mod                 58044  1
evdev                   9728  0
psmouse                30212  0
mousedev               11680  1
parport_pc             35460  1
lp                     12420  0
parport                36104  2 parport_pc,lp
md                     45648  0
reiserfs              264048  4
thermal                13064  0
processor              22908  1 thermal
fan                     4548  0
usbhid                 35552  0
via_rhine              22724  0
sis900                 21632  0
mii                     5760  2 via_rhine,sis900
ehci_hcd               34312  0
ohci_hcd               20740  0
usbcore               118204  4 usbhid,ehci_hcd,ohci_hcd
ide_cd                 41732  0
cdrom                  39904  1 ide_cd
ide_disk               18560  8
ide_generic             1472  0
sis5513                16392  1
ide_core              139028  4 ide_cd,ide_disk,ide_generic,sis5513
unix                   27248  1242
vesafb                  8088  0
capability              4808  0
commoncap               6912  1 capability
vga16fb                12680  1
vgastate                9792  1 vga16fb
softcursor              2496  2 vesafb,vga16fb
cfbimgblt               3008  2 vesafb,vga16fb
cfbfillrect             3968  2 vesafb,vga16fb
cfbcopyarea             4672  2 vesafb,vga16fb
fbcon                  39104  72
tileblit                2432  1 fbcon
font                    8320  1 fbcon
bitblit                 5696  1 fbcon
[/INDENT]

---

### Post by NotJustANewbie on 2005-12-12
My CPU seems to be 100% most of the time... I don't seem to experience any slowness though. GDeskelets did slow my desktop down however... considerably.

---

### Post by Arwyn on 2005-12-12
100% CPU shouldn't slow the computer down. It's the slow IO that is doing it. My computer at home has a virtualy identical setup and runs smoothly. The only major difference in the setup is the motherboard chipset.

Windows on identical hardware does not seem to suffer this problem, which leads me to suspect driver trouble. However I have not heard of trouble with the sis741 chipset under linux.... This is what confuses me.

And if it's driver trouble which driver?

---

