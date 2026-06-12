---
title: "snd-powermac on 9.04 after update"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by daniele_b on 2009-09-13
after dist-upgrade i don't have any sound device, how can i install the snd-powermac?

```
uname -a
Linux pixall.myftp.biz 2.6.24-24-powerpc-smp #1 SMP Sat Jul 25 00:58:36 UTC 2009 ppc GNU/Linux
``````
lsusb
Bus 002 Device 002: ID 05ac:1101 Apple Computer, Inc. Speakers
``````
less /etc/modules | grep snd-
snd-powermac

``````
lsmod
Module                  Size  Used by
ppdev                  11524  0 
lp                     13612  0 
parport                46076  2 ppdev,lp
iptable_filter          3232  0 
ip_tables              16724  1 iptable_filter
x_tables               18308  1 ip_tables
ipv6                  324068  36 
pmac_zilog             22088  0 
serial_core            26848  1 pmac_zilog
nls_cp437               6048  0 
nls_utf8                2272  10 
cifs                  295215  10 
evdev                  14880  3 
uninorth_agp           12108  1 
agpgart                41760  1 uninorth_agp
ext3                  166472  1 
jbd                    63540  1 ext3
mbcache                10404  1 ext3
usbhid                 36612  0 
hid                    48808  1 usbhid
ide_cd                 37508  0 
cdrom                  47292  1 ide_cd
ide_disk               20352  3 
ohci_hcd               41840  0 
ohci1394               41776  0 
sungem                 37700  0 
sungem_phy             13280  1 sungem
ieee1394              111632  1 ohci1394
usbcore               177492  3 usbhid,ohci_hcd
windfarm_core          14704  0 
fuse                   58868  1 

```

---

