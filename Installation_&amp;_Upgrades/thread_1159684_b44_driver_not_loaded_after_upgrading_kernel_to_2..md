---
title: "b44 driver not loaded after upgrading kernel to 2.6.29"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by arielCo on 2009-05-14
Hello,

The title pretty much sums it up. According to lspci, my NIC is a "Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)". After installing linux-headers-*_{all,i386}.deb and linux-image-*_i386.deb from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.3/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.29.3/") (in that order, no errors), I rebooted but the b44 driver for my NIC was not loaded or mentioned in the output from dmesg.

```

$ ls -l /lib/modules/*/kernel/drivers/net/b44.ko
-rw-r--r-- 1 root root 46776 2009-04-16 23:12 /lib/modules/2.6.28-11-generic/kernel/drivers/net/b44.ko
-rw-r--r-- 1 root root 39280 2009-05-11 10:28 /lib/modules/2.6.29-02062903-generic/kernel/drivers/net/b44.ko

``````
$ modinfo /lib/modules/*/kernel/drivers/net/b44.ko
filename:       /lib/modules/2.6.28-11-generic/kernel/drivers/net/b44.ko
version:        2.0
license:        GPL
description:    Broadcom 44xx/47xx 10/100 PCI ethernet driver
author:         Felix Fietkau, Florian Schirmer, Pekka Pietikainen, David S. Miller
srcversion:     D926C0FD72CC929295E14A0
alias:          ssb:v4243id0806rev*
alias:          pci:v000014E4d0000170Csv*sd*bc*sc*i*
alias:          pci:v000014E4d00004402sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004401sv*sd*bc*sc*i*
depends:        ssb,mii
vermagic:       2.6.28-11-generic SMP mod_unload modversions 586 
parm:           b44_debug:B44 bitmapped debugging message enable value (int)

filename:       /lib/modules/2.6.29-02062903-generic/kernel/drivers/net/b44.ko
version:        2.0
license:        GPL
description:    Broadcom 44xx/47xx 10/100 PCI ethernet driver
author:         Felix Fietkau, Florian Schirmer, Pekka Pietikainen, David S. Miller
srcversion:     629FF01A8FCFC1074848876
alias:          ssb:v4243id0806rev*
alias:          pci:v000014E4d0000170Csv*sd*bc*sc*i*
alias:          pci:v000014E4d00004402sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004401sv*sd*bc*sc*i*
depends:        ssb,mii
vermagic:       2.6.29-02062903-generic SMP mod_unload modversions 586 
parm:           b44_debug:B44 bitmapped debugging message enable value (int)

```In general, different sets of modules were loaded by both kernels:
```

$ join -v1 <(< lsmod.2.6.28-11-generic sort) <(< lsmod.2.6.29-02062903-generic sort)
b44 35984 0 
bitblit 13824 1 fbcon
fbcon 46112 0 
font 16384 1 fbcon
ieee80211_crypt 13444 2 ieee80211_crypt_tkip,wl
ieee80211_crypt_tkip 16896 0 
input_polldev 11912 0 
mii 13312 1 b44
softcursor 9984 1 bitblit
ssb 41220 1 b44
tileblit 10752 1 fbcon
wl 1489748 0 

$ join -v2 <(< lsmod.2.6.28-11-generic sort) <(< lsmod.2.6.29-02062903-generic sort)
led_class 3872 1 sdhci
ricoh_mmc 3580 0 
snd_hda_codec 63964 2 snd_hda_codec_idt,snd_hda_intel
snd_hda_codec_idt 56700 1 

```Where should I start looking?

Regards,
ariel

---

