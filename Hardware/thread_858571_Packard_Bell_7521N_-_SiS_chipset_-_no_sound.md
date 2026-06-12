---
title: "Packard Bell 7521N - SiS chipset - no sound"
date: 2008-07-13
forum: Hardware
---

### Post by lion99 on 2008-07-13
I have cross-posted this from the Kubuntu forums, as although lots of people were reading it there, no answers seem to be forthcoming, and I don't think it is anything to do with KDE anyway.

I was posting originally in the Hardy (8.04) thread, and the problem is with the latest version, fully up to date. The machine is a laptop, kernel is 2.6.24-19-generic #1 SMP.

Oh, and I have just noticed something. What is the drm module (I assume Digital Restrictions Management), and why is it present on such an ancient machine?

Original post follows:

...........


This one has me puzzled. It is not my machine, belongs to someone who has never used Linux, so it is
important that I get it fixed, or we may lose a new user.

There is no sound, despite messing about with the settings in KDE. It seems that OSS is being selected on installation, rather than ALSA, which seems to be wrong, but I can't see any way of changing it.

I have checked the usual things.

Output of lspci:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 630 Host (rev 31)
00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:01.4 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS PCI Audio Accelerator (rev 02)
00:01.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:08.0 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:08.1 CardBus bridge: Texas Instruments PCI1225 (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter (rev 31)

Output of lsmod:

Module                  Size  Used by
ipv6                  267780  8
af_packet              23812  2
rfcomm                 41744  2
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
sis                     8320  2
drm                    82452  3 sis
ppdev                  10372  0
speedstep_lib           6532  0
cpufreq_conservative     8712  0
cpufreq_powersave       2688  0
cpufreq_stats           7104  0
cpufreq_userspace       5284  0
cpufreq_ondemand        9740  0
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
container               5632  0
sbs                    15112  0
sbshc                   7680  1 sbs
video                  19856  0
output                  4736  1 video
dock                   11280  0
iptable_filter          3840  0
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
aes_i586               33536  0
dm_crypt               15364  0
dm_mod                 62660  1 dm_crypt
lp                     12324  0
pcnet_cs               39600  1
8390                   11776  1 pcnet_cs
joydev                 13120  0
pcmcia                 40876  1 pcnet_cs
snd_trident            44324  1
gameport               16008  2 snd_trident
snd_ac97_codec        101028  1 snd_trident
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_trident,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_trident,snd_pcm
snd_util_mem            5632  1 snd_trident
snd_mpu401_uart         9728  1 snd_trident
irtty_sir               9728  0
sir_dev                17412  1 irtty_sir
snd_seq_dummy           4868  0
irda                  203068  2 irtty_sir,sir_dev
evdev                  13056  5
crc_ccitt               3072  1 irda
parport_pc             36260  1
parport                37832  3 ppdev,lp,parport_pc
serio_raw               7940  0
psmouse                40336  0
snd_seq_oss            35584  0
snd_seq_midi            9376  0
snd_rawmidi            25760  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
button                  9232  0
battery                14212  0
ac                      6916  0
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  14 snd_trident,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27276  4
rsrc_nonstatic         13696  1 yenta_socket
pcspkr                  4224  0
pcmcia_core            40596  4 pcnet_cs,pcmcia,yenta_socket,rsrc_nonstatic
soundcore               8800  1 snd
shpchp                 34452  0
pci_hotplug            30880  1 shpchp
i2c_sis630              8076  0
sis_agp                10116  1
i2c_core               24832  1 i2c_sis630
agpgart                34760  2 drm,sis_agp
ext3                  136712  3
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0
sr_mod                 17956  0
cdrom                  37408  1 sr_mod
sd_mod                 30720  5
ata_generic             8324  0
pata_acpi               8320  0
floppy                 59588  0
pata_sis               15236  4
ohci_hcd               25348  0
libata                159344  3 ata_generic,pata_acpi,pata_sis
usbcore               146028  2 ohci_hcd
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
thermal                16796  0
processor              36872  1 thermal
fan                     5636  0
fbcon                  42912  0
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  1

It occurs to me that trident drivers might not work with the SiS chipset, but why is the system configuring itself that way, and how could I change it?

All suggestions will be gratefully received.


Alan

---

### Post by RoboJ1M on 2010-04-14
Hi,

Did you ever get anything to work?
I have a Packard Bell 7521N that a friend wants to experiment with Ubuntu Server on, and I can't get any Ubuntu CD to load on it. Everything just hangs with a fading/blank screen immediately after you select Install Ubuntu.

I've tried graphical and alternate installers, ubuntu, Xubuntu (worked the best, still failed with squashFS errors) 

8.04, 8.10 and 9.10 tried.

Did you ever have that problem?

J.

---

