---
title: "VIA VT6421A problems geting my SATA recogniced.."
date: 2008-07-10
forum: Hardware
---

### Post by Celeb on 2008-07-10
Hi, i'm having problems with my PCI SATA controller... i can't see my SATA disks :S, but i see the card:

02:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0e.0 Class 4104: VIA Technologies, Inc. Unknown device 7249 (rev ff)

this is what #lspci shows me.

and this:


root@ubuntu:/home/ubuntu# lsmod 
Module                  Size  Used by
sata_via               12420  0 
ipv6                  267780  8 
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
speedstep_lib           6532  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8712  0 
video                  19856  0 
output                  4736  1 video
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
ac                      6916  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
joydev                 13120  0 
i2c_core               24832  0 
container               5632  0 
serio_raw               7940  0 
button                  9232  0 
intel_agp              25492  1 
evdev                  13056  4 
agpgart                34760  1 intel_agp
shpchp                 34452  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
pci_hotplug            30880  1 shpchp
pcspkr                  4224  0 
psmouse                40336  0 
battery                14212  0 
squashfs               49160  1 
loop                   18948  2 
unionfs                76752  1 
nls_cp437               6656  1 
isofs                  36388  1 
ext3                  136712  0 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
usbhid                 31872  0 
hid                    38784  1 usbhid
sg                     36880  0 
sr_mod                 17956  1 
cdrom                  37408  1 sr_mod
sd_mod                 30720  0 
floppy                 59588  0 
uhci_hcd               27024  0 
ata_piix               19588  1 
pata_acpi               8320  0 
8139too                27520  0 
usbcore               146028  3 usbhid,uhci_hcd
ata_generic             8324  0 
8139cp                 24704  0 
e100                   37388  0 
mii                     6400  3 8139too,8139cp,e100
libata                159344  4 sata_via,ata_piix,pata_acpi,ata_generic
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 

I tryed modprobe sata_via... but it dosen't work.... help me plis..

Thank you verry much..

Celeb

---

### Post by CityofAsh on 2008-09-04
Were you able to get this working?

---

