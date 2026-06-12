---
title: "Modem installation &quot;killed&quot; USB mouse"
date: 2008-07-29
forum: Hardware
---

### Post by Gorstak on 2008-07-29
I have 2 USB ports on my computer (1.1). On first port I plugged 5 port hub and Sagem F@st 800 E4 and Transcend multi card reader on it. On second port I plugged Bluetooth MSI Starkey and Logitech RX600 mouse. I intalled Ubuntu 8.04 (a localized version called cp6Linux) and usb mouse worked perfectly, card reader too. Bluetooth was recognized but i didn't tried it. Sagem modem was not functional. I managed to install the eagle driver for the modem and set up the internet connection but after that usb mouse don't work. Card reader still work, but I can't initialize bluetooth (since I haven't tried it before I can't blame modem for that). Beside that PS2 mouse that is also connected behave a bit chaotic (various random movements and clicks) after modem installation and PS2 keyboard repeat every 3rd or 4th keypress for couple times (also after modem installation - before that worked perfectly). I tried to plug only modem on one port and mouse on other port without hubs and other usb devices but situation remains the same. When I unplug modem, usb mouse works so as PS2 keyboard but if I plug in modem again I  can't estabilish the connection. I even tried to plug mouse in same hub with modem and card reader ('cause they works at the same time) but nothing changes.
I'm an apsolute beginner in Linux world and I hope someone will help me because I don't know what to do.:confused:


[EDIT]

here are the lsusb output

> Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 008: ID 1110:9041 Analog Devices Canada, Ltd (Allied Telesyn) 
Bus 001 Device 007: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 006: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 001 Device 005: ID 0a5c:2101 Broadcom Corp. 
Bus 001 Device 004: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 001: ID 0000:0000 


lsmod output:

> Module                  Size  Used by
xt_TCPMSS               5504  1 
xt_tcpmss               3200  1 
xt_tcpudp               4096  1 
iptable_mangle          3712  1 
pppoe                  14528  2 
pppox                   4876  1 pppoe
af_packet              23812  2 
ppp_generic            29588  6 pppoe,pppox
slhc                    7040  1 ppp_generic
br2684                 10116  1 
isofs                  36388  1 
udf                    88612  0 
lirc_dev               15732  0 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
ppdev                  10372  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8712  0 
dock                   11280  0 
container               5632  0 
video                  19856  0 
output                  4736  1 video
sbs                    15112  0 
sbshc                   7680  1 sbs
battery                14212  0 
ipv6                  267780  10 
iptable_filter          3840  0 
ip_tables              14820  2 iptable_mangle,iptable_filter
x_tables               16132  4 xt_TCPMSS,xt_tcpmss,xt_tcpudp,ip_tables
ac                      6916  0 
lp                     12324  0 
snd_cmipci             38528  5 
gameport               16008  1 snd_cmipci
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_cmipci,snd_pcm_oss
lmpcm_usb               7168  0 
snd_page_alloc         11400  1 snd_pcm
snd_opl3_lib           12928  1 snd_cmipci
snd_hwdep              10500  1 snd_opl3_lib
snd_mpu401_uart         9728  1 snd_cmipci
evdev                  13056  10 
usb_storage            73664  0 
ueagle_atm             34744  0 
usbatm                 20608  2 ueagle_atm
libusual               19108  1 usb_storage
usbhid                 31872  0 
hid                    38784  1 usbhid
hci_usb                16540  0 
bluetooth              61156  6 rfcomm,l2cap,hci_usb
snd_seq_dummy           4868  0 
psmouse                40336  0 
serio_raw               7940  0 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  2 snd_mpu401_uart,snd_seq_midi
pcspkr                  4224  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
nvidia               4718832  32 
bt878                  11832  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device          9612  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
tuner                  42912  0 
tea5767                 6788  1 tuner
tda8290                12420  1 tuner
tuner_simple           10248  1 tuner
mt20xx                 13192  1 tuner
tea5761                 6020  1 tuner
bttv                  175860  1 bt878
via_ircc               27796  0 
ir_common              36100  1 bttv
irda                  203068  1 via_ircc
compat_ioctl32          2304  1 bttv
i2c_algo_bit            7300  1 bttv
snd                    56996  23 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
crc_ccitt               3072  1 irda
videobuf_dma_sg        14980  1 bttv
videobuf_core          18820  2 bttv,videobuf_dma_sg
btcx_risc               5896  1 bttv
i2c_viapro              9876  0 
button                  9232  0 
tveeprom               16656  1 bttv
i2c_core               24832  11 nvidia,tuner,tea5767,tda8290,tuner_simple,mt20xx,tea5761,bttv,i2c_algo_bit,i2c_viapro,tveeprom
soundcore               8800  1 snd
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
videodev               29440  1 bttv
v4l2_common            18304  3 tuner,bttv,videodev
v4l1_compat            15492  2 bttv,videodev
via_agp                11136  1 
agpgart                34760  2 nvidia,via_agp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  1 
cdrom                  37408  1 sr_mod
sd_mod                 30720  5 
floppy                 59588  0 
pata_via               13316  4 
uhci_hcd               27024  0 
ata_generic             8324  0 
pata_acpi               8320  0 
usbcore               146028  9 lmpcm_usb,usb_storage,ueagle_atm,usbatm,libusual,usbhid,hci_usb,uhci_hcd
libata                159344  3 pata_via,ata_generic,pata_acpi
scsi_mod              151436  5 usb_storage,sg,sr_mod,sd_mod,libata
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 



and xorg.conf

> Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection


I don't know what lines are important so I posted all


[EDIT]

This problem is solved! Thanks to dukenukem7 from [www.ubuntu-rs.org](www.ubuntu-rs.org)

solution:
> sudo gedit /etc/modprobe.d/ueagle-atm
then insert
> options ueagle-atm altsetting=1,1,1,1
save and restart. It works!!

---

