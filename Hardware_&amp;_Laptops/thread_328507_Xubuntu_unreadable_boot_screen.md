---
title: "Xubuntu unreadable boot screen"
date: 2006-12-31
forum: Hardware &amp; Laptops
---

### Post by CloseYetFar on 2006-12-31
Hi, When I boot my Xubuntu system the screen right after grub is unreadable. This lasts for about 30 seconds till I get to the login screen which looks fine. Because both the login screen and grub look fine I can fully use the computer. But I'm still wondering why part of the boot is unreadable.

I got the laptop a Sony VAIO PCG-FX240 from a friend who ran Debian on it. He said he had a similar problem, but could not remember how he fixed it. He said it had something to do with the video framebuffer. I believe frambuffering is enabled on my system and want to know how I can disable it.

Can I disable framebuffering by disabling certain modules, and which modules exactly?  

Here is the output from lsmod:

Module                  Size  Used by
freq_table              6048  0 
sonypi                 24252  0 
video                  17540  0 
tc1100_wmi              8324  0 
sony_acpi               6412  0 
sbs                    16804  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
container               5632  0 
button                  7952  0 
battery                11652  0 
asus_acpi              17688  0 
ac                      6788  0 
af_packet              24584  0 
nls_utf8                3200  1 
ntfs                  112116  1 
ipv6                  272288  14 
ext2                   71432  1 
sbp2                   24584  0 
scsi_mod              144648  1 sbp2
lp                     12964  0 
joydev                 11200  0 
pcmcia                 40380  0 
tsdev                   9152  0 
e100                   38020  0 
evdev                  11392  2 
serio_raw               8452  0 
mii                     6912  1 e100
yenta_socket           28812  2 
rsrc_nonstatic         15360  1 yenta_socket
floppy                 63044  0 
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
snd_intel8x0           34844  2 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
psmouse                41352  0 
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
intel_agp              26012  1 
agpgart                34888  2 intel_agp
snd                    58372  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
hw_random               7320  0 
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
i2c_i810                6276  0 
i2c_algo_bit           10376  1 i2c_i810
pcspkr                  4352  0 
i2c_core               23424  2 i2c_ec,i2c_algo_bit
usbhid                 45152  0 
ext3                  142728  1 
jbd                    62228  1 ext3
uhci_hcd               24968  0 
usbcore               134912  3 usbhid,uhci_hcd
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  5 
piix                   11780  1 
generic                 5764  0 
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

Thanks, any info will help.

---

### Post by taurus on 2006-12-31
You can remove the **quiet** from the entry for kernel in /boot/grub/menu.lst if you want to see the start up services...

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

---

