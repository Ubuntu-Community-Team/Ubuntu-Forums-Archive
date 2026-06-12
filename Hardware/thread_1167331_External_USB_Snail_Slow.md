---
title: "External USB Snail Slow"
date: 2009-05-22
forum: Hardware
---

### Post by rompstar on 2009-05-22
I got ubuntu 9.04, my external USB drive that I use for backup works but is very slow, and I do have USB 2.0.  Results of some commands:

raymond@localhost:/etc/initramfs-tools$ lsusb
Bus 002 Device 002: ID 045e:0029 Microsoft Corp. IntelliMouse Optical
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0d49:3100 Maxtor Hi-Speed USB-IDE Bridge Controller
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




raymond@localhost:/etc/initramfs-tools$ lsmod
Module                  Size  Used by
ecb                    10752  1 
binfmt_misc            16776  1 
ppdev                  15492  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
video                  25360  0 
output                 11008  1 video
input_polldev          11784  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
i2c_amd756             13828  0 
pcspkr                 10496  0 
shpchp                 40340  0 
k8temp                 12416  0 
amd_rng                10500  0 
sha256_generic         20352  0 
aes_i586               15744  3759 
aes_generic            35880  1 aes_i586
cbc                    11648  3757 
usbhid                 42464  0 
usb_storage            82752  1 
dm_crypt               20868  1 
tg3                   131460  0 
aic7xxx               134488  0 
scsi_transport_spi     29824  1 aic7xxx
fbcon                  45856  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13696  1 fbcon
softcursor              9984  1 bitblit


raymond@localhost:/etc/initramfs-tools$ sudo hdparm -tT /dev/sdb1

/dev/sdb1:
 Timing cached reads:     2 MB in  2.02 seconds = 1012.08 kB/sec
 Timing buffered disk reads:    4 MB in  4.06 seconds = 1009.68 kB/sec


raymond@localhost:/etc/initramfs-tools$ sudo modprobe -r ehci-hcd ; sudo modprobe ehci-hcd
FATAL: Module ehci_hcd not found.
FATAL: Module ehci_hcd not found.
raymond@localhost:/etc/initramfs-tools$ 



any ideas ?

---

### Post by rompstar on 2009-05-24
nothing ? nobody has any clue ?

:?

---

