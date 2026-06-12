---
title: "sound card problems (YAMAHA719)"
date: 2005-08-04
forum: Hardware &amp; Laptops
---

### Post by ANU on 2005-08-04
my system:

OS: Ubuntu 5.04
sound card: YMF719E-S (Yamaha719)
....

i get the error: device /dev/dsp can't be opened
ls -al /dev/dsp
and there is no dsp
how can i make my souncard work?
pls help me with step by step instruction... im new in linux ;)

thanks

---

### Post by ANU on 2005-08-08
i still cant use my soundcard .. pls help me out
```

#lsmod 
Module                  Size  Used by
snd_pcm_oss            47652  0 
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  1 snd_pcm_oss
snd_page_alloc          9604  1 snd_pcm
snd_opl3_lib           10112  0 
snd_timer              23300  2 snd_pcm,snd_opl3_lib
snd_hwdep               9220  1 snd_opl3_lib
snd_mpu401_uart         7168  0 
snd_rawmidi            22944  1 snd_mpu401_uart
snd_seq_device          8332  2 snd_opl3_lib,snd_rawmidi
snd                    50276  9 snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  1 snd
proc_intf               4100  0 
freq_table              4100  0 
cpufreq_userspace       4572  0 
cpufreq_ondemand        6172  0 
cpufreq_powersave       1920  0 
apm                    19948  2 
ipv6                  229504  11 
uhci_hcd               30224  0 
ohci_hcd               19848  0 
ehci_hcd               29444  0 
usbcore               107384  3 uhci_hcd,ohci_hcd,ehci_hcd
ne2k_pci               10080  0 
8390                    9984  1 ne2k_pci
i2c_via                 4228  0 
i2c_algo_bit            9224  1 i2c_via
i2c_core               21264  1 i2c_algo_bit
pci_hotplug            30512  0 
via_agp                 9216  1 
agpgart                31784  1 via_agp
analog                 10784  0 
ns558                   5632  0 
gameport                4608  2 analog,ns558
floppy                 54864  0 
pcspkr                  3816  0 
rtc                    12216  0 
md                     43856  0 
dm_mod                 53116  1 
capability              5000  0 
commoncap               7808  1 capability
evdev                   9088  0 
psmouse                19336  0 
mousedev               11160  0 
parport_pc             34372  1 
lp                     10792  0 
parport                33480  2 parport_pc,lp
ide_cd                 38532  0 
cdrom                  36508  1 ide_cd
ext3                  120968  1 
jbd                    54168  1 ext3
ide_generic             1664  0 
via82cxxx              12956  1 
ide_disk               18176  3 
ide_core              118988  4 ide_cd,ide_generic,via82cxxx,ide_disk
unix                   26164  336 
processor              22708  0 
fbcon                  34048  0 
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0 
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb
#ls -al /lib/modules/2.6.10-5-386/kernel/sound/
total 60
drwxr-xr-x  11 root root  4096 2005-08-04 21:37 .
drwxr-xr-x  10 root root  4096 2005-08-03 20:52 ..
drwxr-xr-x   4 root root  4096 2005-08-04 21:37 core
drwxr-xr-x   6 root root  4096 2005-08-04 21:37 drivers
drwxr-xr-x   3 root root  4096 2005-08-04 21:37 i2c
drwxr-xr-x  10 root root  4096 2005-08-04 21:37 isa
drwxr-xr-x   4 root root  4096 2005-08-04 21:37 oss
drwxr-xr-x  15 root root  4096 2005-08-04 21:37 pci
drwxr-xr-x   4 root root  4096 2005-08-03 20:52 pcmcia
-rw-r--r--   1 root root 12624 2005-06-24 23:22 soundcore.ko
drwxr-xr-x   3 root root  4096 2005-08-04 21:37 synth
drwxr-xr-x   3 root root  4096 2005-08-04 21:37 usb

```

---

### Post by mo_x on 2005-08-08
From the ALSA website I can see you need the module snd-opl3-sa2. Try to load it manually with the following command:
sudo modprobe snd-opl3-sa2

Try some searching on google and in this forum on opl3-sa2.

---

### Post by ANU on 2005-08-10
```
#modprobe snd-opl3-sa2
FATAL: Module snd_opl3_sa2 not found.

```
what now?
pls help :((

---

### Post by mo_x on 2005-08-10
My mistake, module has a slightlly different name, it should be:
sudo modprobe snd-opl3sa2

---

