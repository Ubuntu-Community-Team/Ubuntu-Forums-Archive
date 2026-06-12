---
title: "libata – ata_generic module causing slow ide transfer speeds"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by asw3 on 2007-05-07
for the last two  days attempting  to get Ubuntu 7.04 desktop i386 up and running on my “ gigabyte 965P-DS3P ”  ( P965 / ICH8R ) motherboard .. after the initial setup i experienced  problems with extremely slow  DVD  transfer rates ... (i.e. playing an avi file of dvd, the  playback would  stagger every 25 seconds)...

i tracked the problem down the kernel using the libata driver  “ata_generic” instead of  “ pata_jmicron” for the ide devices... for example output of “lsmod | grep -i ^libata” was:
libata                125208  4 pata_jmicron,ata_generic,ata_piix,ahci



to fix the problem i recompiled the kernel and removed the unwanted “ata_generic” module. (i didn't know why it was using “ahci” so i removed it as well)  ..  output of “lsmod | grep -i ^libata”  is now:
libata                123416  2 pata_jmicron,ata_piix

well, the transfer rate problem  does not seem to appear anymore... . 


my question .... is there a way to stop these unwanted libata modules from loading, without going through the hassle of recompiling the kernel?

---

### Post by satreth on 2008-01-27
Hi, it's quite some time since you posted, but the information could be helpful also to others.
To avoid recompiling, you can blacklist the unwanted modules. Since it is modules loaded very early at boot time you have to do that in the initramfs modules file. Just add: **blacklist ata_generic** to **/etc/initramfs-tools/modules**. Not sure if that is necessary, but I also added the pata controller's module to the file (simply adding the module's name before the blacklisted one).
Then recreate the initramfs with 
```

$ sudo update-initramfs -u

```
**Careful** blacklisting the wrong modules could make your system unbootable

this should be it.

---

### Post by assan on 2008-02-03
Hi,

I have problem with dma on sata disk.
After sudo hdparm -d1 /dev/sda
I receive:
/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

I followed your advice how to blacklist “ata_generic” module and after sudo update-initramfs -u

Now, output “lsmod | grep -i ^libata” is:
libata                125168  2 ata_generic,sata_sil

I have no idea why there is stil ata_generic. There is one difference. Before sata_sil was first.
Speed is little lower.

My initramfs modules file have this lines

sata_sil

blacklist ata_generic

Please give me some suggestions.

---

### Post by satreth on 2008-02-05
Hi, 
Apparently on sata disks it is not possible to enable DMA via hdparm (it is done automatically). 

About the ata_generic module: I also have it still loaded. The goal of blacklisting it in the initramfs was to not have it loaded before the pata/sata driver. The module can still be loaded later (and apparently is). To totally remove it you probably have to blacklist it in the standard modules file (/etc/modules) too.

ciao

---

### Post by pokipoki08 on 2008-07-04
Thanks for this tip. I managed to increase my hdd Timing cached reads to 2528.43 MB/sec. Here's what I did.

added this line in file [COLOR="Blue"]/etc/initramfs-tools/modules[/COLOR]
```
blacklist ata_generic
```

and re-created initramfs
```
sudo update-initramfs -u
```

Copying large files or running unrar no longer spikes the CPU or slows down the system.

---

