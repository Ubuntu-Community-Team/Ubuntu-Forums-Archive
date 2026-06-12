---
title: "Es1869 Audio Not Working For Hardy"
date: 2008-05-06
forum: Hardware
---

### Post by Relicman on 2008-05-06
Hi this is driving me nuts. Laptop Compaq Armada 1750 audio is not working on 8.04 Hardy. I have sound enabled and the auido card appears in the Audio Control Preferences.

lspci does not register the audio card
aplay -l does show the audio card

Running alsamixer from the command line shows the master volume control as being off but set at maximum. I cannot alter the state of the master control. Small audio icon on the desktop shows the audio as being non-muted.

One other issue which may be related. Not only do I have no sound, but I cannot get any audio application to play an MP3 file or any other audio for that matter. IE when playing audio the application does not play or time the song. 

Any help appreciated

---

### Post by ewand on 2008-05-06
Pretty sure ES1869 isn't PCI, it's ISA - so you shouldn't expect it to show up in lspci. It sounds like it's almost working, but as a sanity check, the first thing I would do is type
```
lsmod
```
and make sure I get snd-es1688 (think that's the right driver for ES1689) in the list. You should also see something (rather than nothing) when you type
```
cat /proc/asound/cards
```
You say it's not working on Hardy - was it working on Gutsy?
--ewan

---

### Post by Relicman on 2008-05-09
Hi Ewan,

Many thanks for your input: Below are the results:
root@vinny-laptop:~# lsmod
Module                  Size  Used by
ipv6                  267780  15 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
apm                    22616  2 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
snd_es18xx             35124  2 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_es18xx,snd_pcm_oss
snd_page_alloc         11400  1 snd_pcm
snd_opl3_lib           12928  1 snd_es18xx
snd_hwdep              10500  1 snd_opl3_lib
snd_mpu401_uart         9728  1 snd_es18xx
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device          9612  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  16 snd_es18xx,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
lp                     12324  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
rt2500pci              20352  0 
rt2x00pci              11264  1 rt2500pci
rt2x00lib              22528  2 rt2500pci,rt2x00pci
rfkill                  8592  1 rt2x00lib
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
mac80211              165652  3 rt2500pci,rt2x00pci,rt2x00lib
cfg80211               15112  1 mac80211
eeprom_93cx6            3200  1 rt2500pci
pcmcia                 40876  0 
evdev                  13056  1 
serio_raw               7940  0 
psmouse                40336  0 
irtty_sir               9728  0 
sir_dev                17412  1 irtty_sir
yenta_socket           27276  3 
shpchp                 34452  0 
irda                  203068  2 irtty_sir,sir_dev
pcspkr                  4224  0 
parport_pc             36260  1 
rsrc_nonstatic         13696  1 yenta_socket
pci_hotplug            30880  1 shpchp
i2c_piix4               9612  0 
crc_ccitt               3072  1 irda
intel_agp              25492  1 
parport                37832  3 ppdev,lp,parport_pc
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
agpgart                34760  1 intel_agp
i2c_core               24832  1 i2c_piix4
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
pata_acpi               8320  0 
ata_generic             8324  0 
ata_piix               19588  2 
uhci_hcd               27024  0 
libata                159344  3 pata_acpi,ata_generic,ata_piix
floppy                 59588  0 
usbcore               146028  2 uhci_hcd
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 
root@vinny-laptop:~# cat /proc/asound/cards
 0 [ES1869         ]: ES1869 - ESS AudioDrive ES1869
                      ESS AudioDrive ES1869 at 0x220, irq 5, dma1 1, dma2 5

Hope this helps. 

I never got the laptop to install Gutsy, but did get the audio to work on Breezy. I had to maks some mods to the following:
1) /etc/modules
lp
mousedev
psmouse
snd-es18xx

2) /etc/modprobe.d/alsa-base
alias char-major-116 snd
alias snd-card-0 snd es-es18xx
options snd es18xx index=0 enable=1 isapnp=0 port=0x220 mpu_port=0x388 fm_port=0x330 irq=5 dma1=1 dma2=5

Have tried this for Hardy but nogo.

Vince

---

### Post by tekrytor on 2008-05-22
> **ewand said:**
> Pretty sure ES1869 isn't PCI, it's ISA - so you shouldn't expect it to show up in lspci. It sounds like it's almost working, but as a sanity check, the first thing I would do is type
```
lsmod
```
and make sure I get snd-es1688 (think that's the right driver for ES1689) in the list. You should also see something (rather than nothing) when you type
```
cat /proc/asound/cards
```
:guitar:You say it's not working on Hardy - was it working on Gutsy?
--ewan

Hi Ewan,

New Ubuntu Studio user here. I went through a lot of strangeness to get UbStudio 7.10 running on my old Dell Inspiron 7000 notebook. It works great except for two things; one is the wifi (ethernet works just by pluging in the cable so here I am) and the other is no sound via internal ESS1968. It acts like its installed drivers, but zero audio. Apps open and appear to run, but no audio at all is heard. I saw this thread and thought it looked similar enough to ask here about the ESS1968.

When I run the first command you posted, I get the following, but the second command returns "no sound cards". Any tips?

Thanks,
Steve

user@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc            13320  1 
ipv6                  281444  8 
af_packet              25352  2 
rfcomm                 43672  2 
l2cap                  26752  11 rfcomm
bluetooth              58980  4 rfcomm,l2cap
apm                    23256  2 
ppdev                  10244  0 
cpufreq_userspace       5280  0 
cpufreq_conservative     8072  0 
cpufreq_stats           7488  0 
cpufreq_ondemand        9612  0 
cpufreq_powersave       2688  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
lp                     13252  0 
loop                   19588  0 
snd_es1968             30880  0 
gameport               17672  1 snd_es1968
snd_ac97_codec        100772  1 snd_es1968
ac97_bus                3456  1 snd_ac97_codec
snd_pcm_oss            44928  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80644  3 snd_es1968,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_es1968,snd_pcm
snd_mpu401_uart         9856  1 snd_es1968
snd_seq_dummy           4740  0 
snd_seq_oss            33792  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54128  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ehci_hcd               36108  0 
ohci_hcd               22788  0 
joydev                 11456  0 
snd                    55172  11 snd_es1968,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
asix                   18688  0 
usbnet                 20360  1 asix
mii                     6528  2 asix,usbnet
parport_pc             37796  1 
parport                38216  3 ppdev,lp,parport_pc
soundcore               9312  1 snd
pcmcia                 41644  0 
radio_maestro           9088  0 
videodev               29568  1 radio_maestro
v4l2_common            18560  1 videodev
v4l1_compat            15364  1 videodev
i2c_piix4              10124  0 
yenta_socket           27660  3 
intel_agp              25748  1 
psmouse                40208  0 
serio_raw               8196  0 
pcspkr                  4352  0 
rsrc_nonstatic         14080  1 yenta_socket
compat_ioctl32          2304  1 radio_maestro
agpgart                35284  1 intel_agp
i2c_core               26880  1 i2c_piix4
pcmcia_core            41776  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 34964  0 
pci_hotplug            33460  1 shpchp
evdev                  11136  1 
ext3                  134536  1 
jbd                    59688  1 ext3
mbcache                 9860  1 ext3
sg                     36764  0 
sr_mod                 17956  0 
sd_mod                 30976  3 
cdrom                  37664  1 sr_mod
ata_generic             8580  0 
ata_piix               17668  2 
uhci_hcd               26512  0 
libata                125424  2 ata_generic,ata_piix
floppy                 63428  0 
usbcore               139912  6 ehci_hcd,ohci_hcd,asix,usbnet,uhci_hcd
scsi_mod              148844  4 sg,sr_mod,sd_mod,libata
fuse                   48404  1 
apparmor               41624  0 
commoncap               8320  1 apparmor
user@ubuntu:~$ 
user@ubuntu:~$ 
user@ubuntu:~$ cat /proc/asound/cards
--- no soundcards ---
user@ubuntu:~$

---

