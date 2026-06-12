---
title: "SCSI under linux troubleshooting"
date: 2007-09-24
forum: Hardware &amp; Laptops
---

### Post by damir123 on 2007-09-24
Hi,

I have a problem with my scsi device on one computer. I was working normally before servers motherboard failed, it has been replaced but external tape device doesn't work.

Here is the config and symptoms, please direct me to the docs if there are some relevant, i couldnt find anything useful...

The computer is breezy installation on HP 380DL, it will probably be upgraded to gutsy in a few months but ih as worked wery nice for the past two yeaers. It has HP 488 ultirium II external tape device connected to the external scsi port.

Server has Smart Array 6i controller, and it usess cciss module in linux.

In scsi controllers bios menu tape drive is recognized. 

The system boots from raid array connected to this scsi controller.

> cat /proc/scsi/scsi 
Attached devices:


>lsmod
ipv6                  264000  37
floppy                 60564  0
pcspkr                  3880  0
tpm_nsc                 6912  0
tpm_atmel               5792  0
tpm                    10464  2 tpm_nsc,tpm_atmel
hw_random               5588  0
pci_hotplug            28412  0
dm_mod                 59232  1
tsdev                   8000  0
evdev                   9920  0
psmouse                30628  0
mousedev               12132  0
parport_pc             36356  0
lp                     12548  0
parport                37384  2 parport_pc,lp
md                     47536  0
reiserfs              265712  1
thermal                13320  0
processor              23816  1 thermal
fan                     4708  0
usbhid                 36096  0
cciss                  54052  3
scsi_mod              137896  2 st,cciss
tg3                   100388  0
ehci_hcd               35816  0
uhci_hcd               32720  0
usbcore               121308  4 usbhid,ehci_hcd,uhci_hcd
ide_cd                 42148  0
cdrom                  40096  1 ide_cd
ide_generic             1600  0
piix                   10980  1
ide_core              140628  3 ide_cd,ide_generic,piix
unix                   29392  100
vesafb                  8216  0
capability              4936  0
commoncap               7040  1 capability
vga16fb                12840  1
vgastate                9888  1 vga16fb
softcursor              2496  2 vesafb,vga16fb
cfbimgblt               3168  2 vesafb,vga16fb
cfbfillrect             4096  2 vesafb,vga16fb
cfbcopyarea             4832  2 vesafb,vga16fb
fbcon                  38880  71
tileblit                2592  1 fbcon
font                    8448  1 fbcon
bitblit                 5856  1 fbcon


In /dev/cciss/ folder there is no entry for the tape (it used to be visible under /dev/st0)


If you are reading please point me to the relevant docs or drivers so i can get the tape drive running again...


Thanks,
Damir

---

