---
title: "Sonix SN9C120a webcam installation"
date: 2008-02-17
forum: Hardware &amp; Laptops
---

### Post by haley0918 on 2008-02-17
i just got my pc setup with ubuntu 7.10 and trying to setup my webcam as described in the title. i tried with the drivers in the synaptic package and the gspcav1 and still got none of them working. but when i boot from the cd with the webcam plugged in, it works. is there anyway to show which driver is used by the auto configuration from livecd for my webcam?

---

### Post by haley0918 on 2008-02-17
nobody has any answer to this???

---

### Post by haley0918 on 2008-02-17
these are some debugs that i can come up with.
```
cky@cky-desktop:~$ dmesg | tail
[  100.834701] usb 1-1: USB disconnect, address 3
[  100.834884] usb 1-1: Disconnecting SN9C1xx PC Camera...
[  100.834888] usb 1-1: V4L2 device /dev/video0 deregistered
[  105.604317] usb 1-1: new full speed USB device using uhci_hcd and address 4
[  105.765136] usb 1-1: configuration #1 chosen from 1 choice
[  105.769996] usb 1-1: SN9C120 PC Camera Controller detected (vid:pid 0x0C45:0x613C)
[  105.796932] usb 1-1: HV7131R image sensor detected
[  106.116090] usb 1-1: Initialization succeeded
[  106.116148] usb 1-1: V4L2 device registered as /dev/video0
[  106.116151] usb 1-1: Optional device control through 'sysfs' interface disabled

```
```
cky@cky-desktop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 05e3:000b Genesys Logic, Inc. Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0c45:613c Microdia 
Bus 001 Device 001: ID 0000:0000  

```
```
cky@cky-desktop:~$ lsmod
Module                  Size  Used by
nls_cp437               6784  1 
isofs                  36412  1 
udf                    87204  0 
ipv6                  273892  8 
af_packet              24840  2 
radeon                125472  2 
drm                    83348  3 radeon
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
speedstep_lib           6404  0 
cpufreq_conservative     8072  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  0 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
video                  18060  0 
sbs                    19592  0 
container               5504  0 
ac                      6148  0 
dock                   10656  0 
button                  8976  0 
battery                11012  0 
lp                     12580  0 
gspca                 608336  0 
snd_via82xx            29336  1 
gameport               16776  1 snd_via82xx
snd_ac97_codec        100644  1 snd_via82xx
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9600  1 snd_via82xx
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
sn9c102               120708  0 
compat_ioctl32          2304  1 sn9c102
videodev               29312  2 gspca,sn9c102
v4l1_compat            15364  1 videodev
v4l2_common            18432  2 sn9c102,videodev
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               8068  0 
psmouse                39952  0 
i2c_viapro             10004  0 
snd                    54660  13 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
i2c_core               26112  1 i2c_viapro
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
via_agp                11264  1 
agpgart                35016  2 drm,via_agp
evdev                  11136  3 
usbhid                 29536  0 
hid                    28928  1 usbhid
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32672  1 
cdrom                  37536  1 ide_cd
ide_disk               18560  7 
sata_via               12548  0 
floppy                 60004  0 
via_rhine              25992  0 
mii                     6528  1 via_rhine
ehci_hcd               36492  0 
ata_generic             8452  0 
libata                125168  2 sata_via,ata_generic
scsi_mod              147084  1 libata
uhci_hcd               26640  0 
usbcore               138632  6 gspca,sn9c102,usbhid,ehci_hcd,uhci_hcd
via82cxxx              10372  0 [permanent]
ide_core              116804  3 ide_cd,ide_disk,via82cxxx
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  7 
apparmor               40728  0 
commoncap               8320  1 apparmor

```

camorama still says that it cannot connect to the webcam and ask to check connection.

---

### Post by haley0918 on 2008-02-17
anyone please help me to get this driver working???

---

### Post by intel on 2008-02-20
there are probably 2 conflicting drivers for your webcam
gspca & sn9c102
one of them is working & one of them is not working 


first unload both drivers
#rmmod gspca
#rmmod sn9c102

then load one and test webcam
#modprobe gspca
test if webcam works

if it does'nt, 
#rmmod gspca
#modprobe sn9c102
test if webcam works

(you can also test this on the live CD)

---

### Post by sayantandas on 2008-03-29
[QUOTE=intel;4368749]there are probably 2 conflicting drivers for your webcam
gspca & sn9c102
one of them is working & one of them is not working 


first unload both drivers
#rmmod gspca
#rmmod sn9c102

then load one and test webcam
#modprobe gspca
test if webcam works

if it does'nt, 
#rmmod gspca
#modprobe sn9c102 

thanks  a milliion :)
u have been very helpfful
i had been surfing for days to find the solution
and it was just two steps....dint realize my drivers were conflicting
thanks again

---

### Post by sayantandas on 2008-03-30
hi... 
i'm having issues when the computer restarts...
i have go through the process all over again. is there any way to block the sn9c102 driver permanently ?

---

