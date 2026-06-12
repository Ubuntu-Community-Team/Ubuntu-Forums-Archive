---
title: "Problem with sound on dell inspiron 4100"
date: 2005-01-06
forum: Hardware &amp; Laptops
---

### Post by pingo on 2005-01-06
When I installed ubuntu my sound card did not automatically configure. this is the first time this has happened to me it did not happen for redhat 8,9 mandrake 9 or fedora 1&2 how can I make it work?

---

### Post by pingo on 2005-01-06
PS. The soundcard appeared under the live cd

---

### Post by fng on 2005-01-06
It could help if you told us what sound card you have :)
Also type the command 'lsmod' in the console and post the output here.

---

### Post by pingo on 2005-01-06
from lsmod
 >  Module                  Size  Used by
snd_seq_oss            29440  0 
snd_seq_midi_event      7552  1 snd_seq_oss
snd_seq                46608  4 snd_seq_oss,snd_seq_midi_event
acpi                    5900  0 
proc_intf               3968  0 
freq_table              4356  1 acpi
cpufreq_userspace       5336  2 
cpufreq_powersave       2048  0 
ipv6                  230020  8 
ds                     17796  4 
button                  6936  0 
ac                      5132  0 
battery                 9740  0 
af_packet              20872  2 
yenta_socket           19328  0 
pcmcia_core            63156  2 ds,yenta_socket
3c59x                  36776  0 
snd_intel8x0m          18632  0 
snd_intel8x0           33068  0 
snd_ac97_codec         59268  2 snd_intel8x0m,snd_intel8x0
snd_pcm_oss            48168  0 
snd_mixer_oss          16640  1 snd_pcm_oss
snd_pcm                85540  3 snd_intel8x0m,snd_intel8x0,snd_pcm_oss
snd_timer              23172  2 snd_seq,snd_pcm
snd_page_alloc         11144  3 snd_intel8x0m,snd_intel8x0,snd_pcm
gameport                4736  1 snd_intel8x0
snd_mpu401_uart         7296  1 snd_intel8x0
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  3 snd_seq_oss,snd_seq,snd_rawmidi
snd                    50660  13 snd_seq_oss,snd_seq_midi_event,snd_seq,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  1 snd
uhci_hcd               29328  0 
usbcore               104292  3 uhci_hcd
pci_hotplug            30640  0 
intel_agp              20512  1 
agpgart                31784  1 intel_agp
floppy                 54996  0 
irtty_sir               8320  0 
sir_dev                18092  1 irtty_sir
irda                  167360  2 irtty_sir,sir_dev
crc_ccitt               2432  1 irda
rtc                    12216  0 
pcspkr                  3816  0 
md                     44744  0 
dm_mod                 51068  1 
capability              4872  0 
commoncap               7168  1 capability
parport_pc             32064  1 
lp                     10436  0 
parport                37320  2 parport_pc,lp
ide_cd                 38276  0 
cdrom                  35872  1 ide_cd
tsdev                   7168  0 
mousedev               10124  1 
joydev                  9536  0 
evdev                   9088  1 
psmouse                17800  0 
ext3                  109544  2 
jbd                    54552  1 ext3
ide_generic             1664  0 
piix                   12576  1 
ide_disk               16768  4 
ide_core              125272  4 ide_cd,ide_generic,piix,ide_disk
unix                   25904  898 
fan                     4236  0 
thermal                13200  0 
processor              17712  2 acpi,thermal
font                    8576  0 
vesafb                  6688  0 
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb
 
 
 my audio card is dected as 
  Multimedia audio controller: Intel Corp. 82801CA/CAM AC'97 Audio Controller (rev 01)
 from lspci
 this seems correct from what I remember from seting sound up under Beos

---

### Post by xhaker on 2005-01-06
Try this:
```
sudo rm /lib/modules/`uname -r`/kernel/sound/pci/snd-intel8x0m.ko
sudo shutdown -r now
``` 

From what i can see your system is using two drivers for the same device.
That happenned to me too. Got it fixed deleting the experimental driver.

---

### Post by pingo on 2005-01-07
tried that, it didn't work. when I booted there was some message from alsa that it had not detected a soundcard

---

