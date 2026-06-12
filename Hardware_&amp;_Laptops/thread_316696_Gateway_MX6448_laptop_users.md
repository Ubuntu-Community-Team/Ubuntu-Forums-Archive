---
title: "Gateway MX6448 laptop users"
date: 2006-12-11
forum: Hardware &amp; Laptops
---

### Post by DavidGX on 2006-12-11
Has anyone with this laptop gotten the sound to work in ubuntu yet?

(Please don't direct me to the ultra-mega-super-duper-sound-guide because it provides no solutions for me. I just need to know if anyone here with this laptop has gotten sound to work.)

Thanks.

---

### Post by ReaderRat on 2006-12-11
You might check & see if your laptop or a similar one has been tested for that....
[**HERE**](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=LaptopTesting&titlesearch=Titles)

---

### Post by Hakachukai on 2008-04-08
Yes, I have a MX6448, and my sound works.

To get it to work I had to compile kernel version 2.6.22-Rc5
and I had to install ALSA

I don't know what options were compiled into that kernel becuse a friend compiled it for me, but that's what it took to get sound working on this machine. I also found the sound guid to be of no help.

Here is a copy of my kernel modules that I have loaded. 

Module                  Size  Used by
ndiswrapper           190680  0
rfcomm                 41432  0
l2cap                  25344  5 rfcomm
bluetooth              56676  4 rfcomm,l2cap
ppdev                   9860  0
radeon                123872  1
drm                    85204  2 radeon
powernow_k8            12736  1
cpufreq_userspace       4832  1
cpufreq_stats           6568  0
cpufreq_powersave       2240  0
cpufreq_ondemand        9036  0
freq_table              5216  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     7624  0
video                  17416  0
sbs                    19208  0
button                  8400  0
battery                10628  0
container               4992  0
ac                      5636  0
asus_acpi              16604  0
af_packet              23944  2
nls_iso8859_1           4608  1
nls_cp437               6272  1
vfat                   13696  1
fat                    54684  1 vfat
nls_utf8                2560  1
ntfs                  107200  1
dm_mod                 59776  0
md_mod                 83348  1
capability              5384  0
commoncap               7808  1 capability
sr_mod                 17508  0
sbp2                   23880  0
scsi_mod              147888  2 sr_mod,sbp2
joydev                 10944  0
tsdev                   8896  0
parport_pc             38000  0
lp                     12416  0
parport                37704  3 ppdev,parport_pc,lp
psmouse                40464  0
pcmcia                 42028  0
pcspkr                  3520  0
yenta_socket           27532  1
rsrc_nonstatic         14464  1 yenta_socket
pcmcia_core            41496  3 pcmcia,yenta_socket,rsrc_nonstatic
rtc                    13848  0
serio_raw               7748  0
sky2                   45064  0
i2c_piix4               9228  0
i2c_core               26368  1 i2c_piix4
shpchp                 34964  0
pci_hotplug            33288  1 shpchp
ati_agp                 9932  0
agpgart                34956  2 drm,ati_agp
evdev                  10752  2
ext3                  135752  1
jbd                    62952  1 ext3
mbcache                 9476  1 ext3
ide_generic             1664  0 [permanent]
ohci1394               36528  0
ieee1394               97528  2 sbp2,ohci1394
ehci_hcd               33100  0
ohci_hcd               22788  0
usbcore               134500  4 ndiswrapper,ehci_hcd,ohci_hcd
ide_cd                 41312  0
cdrom                  37232  2 sr_mod,ide_cd
ide_disk               18048  5
generic                 5508  0 [permanent]
atiixp                  6672  0 [permanent]
thermal                14216  0
processor              26824  2 powernow_k8,thermal
fan                     5444  0
vga16fb                13196  0
vgastate                9408  1 vga16fb


hope that helps

---

