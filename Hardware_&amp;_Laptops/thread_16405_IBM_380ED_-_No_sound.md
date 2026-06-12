---
title: "IBM 380ED - No sound"
date: 2005-02-21
forum: Hardware &amp; Laptops
---

### Post by iminj on 2005-02-21
I installed 'warty' on my IBM 380ED, and can't get the soundcard recognized. I used to have Mandrake 10.0 on this laptop, and I was able to activate sound using the "sndconfig" utility, but I don't see this option with ubuntu.

Google searches seem to indicate that with ubuntu I have to modprobe the device (cs4232) ... and here's what I get:


1st attempt:

$ modprobe snd-cs4232
FATAL: Error inserting snd_cs4232 (/lib/modules/2.6.8.1-5-386/kernel/sound/isa/cs423x/snd-cs4232.ko): Operation not permitted

2nd try:

$ modprobe cs4232
FATAL: Error inserting cs4232 (/lib/modules/2.6.8.1-5-386/kernel/sound/oss/cs4232.ko): Operation not permitted

I decided to see just what modules are on the system, and lsmod returned this:

$ sudo lsmod
Module                  Size  Used by
snd_opl3_lib            9728  0
snd_hwdep               9120  1 snd_opl3_lib
snd_cs4231_lib         24960  0
snd_pcm_oss            48296  0
snd_mixer_oss          16640  1 snd_pcm_oss
snd_pcm                85540  2 snd_cs4231_lib,snd_pcm_oss
snd_timer              23300  3 snd_opl3_lib,snd_cs4231_lib,snd_pcm
snd_page_alloc         11144  2 snd_cs4231_lib,snd_pcm
snd_mpu401_uart         7296  0
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  2 snd_opl3_lib,snd_rawmidi
snd                    50660  10 snd_opl3_lib,snd_hwdep,snd_cs4231_lib,snd_pcm_o ss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
ad1848                 30460  0
uart401                11460  0
sound                  75308  2 ad1848,uart401
soundcore               9824  2 snd,sound
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
ipv6                  230148  8
af_packet              20872  2
pcnet_cs               18356  1
8390                    9984  1 pcnet_cs
crc32                   4608  1 8390
serial_cs               9628  1
ds                     17796  6 pcnet_cs,serial_cs
i82365                 18896  2
uhci_hcd               29328  0
ohci_hcd               19460  0
ehci_hcd               27780  0
usbcore               104292  3 uhci_hcd,ohci_hcd,ehci_hcd
pd6729                  8320  0
pcmcia_core            63156  5 pcnet_cs,serial_cs,ds,i82365,pd6729
irtty_sir               8320  0
sir_dev                18092  1 irtty_sir
irda                  167360  2 irtty_sir,sir_dev
crc_ccitt               2432  1 irda
floppy                 54996  0
pcspkr                  3816  0
rtc                    12216  0
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
tsdev                   7168  0
ide_cd                 38276  0
cdrom                  35872  1 ide_cd
evdev                   9216  0
mousedev               10124  1
psmouse                17800  0
ext3                  109672  1
jbd                    54552  1 ext3
ide_generic             1664  0
piix                   12576  1
ide_disk               16768  3
ide_core              125272  4 ide_cd,ide_generic,piix,ide_disk
unix                   26160  676
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb

I am not sure how to read the above, but clearly there is NO cs4232 module. Does anyone know what cs_4231_lib is  ... and is it useful to help me get this problem solved? Also, I see numerous "snd" modules, although I don't see any alsa modules. Synaptic reports that I have the following alsa packages installed:

alsa-base
alsa-headers
alsa-utils
libpt-plugins-alsa


Any assistance will be greatly appreciated. 
Thanks ! - iminj

---

### Post by iminj on 2005-02-22
I'm not sure if this is relevant to my sound issue (still unresolved), but I noticed the following message displays during the system boot sequence:

"ACPI: Unable to locate RSDP"

thnx - iminj

---

