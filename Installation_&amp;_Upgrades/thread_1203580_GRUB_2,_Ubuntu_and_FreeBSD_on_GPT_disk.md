---
title: "GRUB 2, Ubuntu and FreeBSD on GPT disk"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by Jonie on 2009-07-03
I just did some GRUB 2 testing and want to share my experience.

First, I installed (rather restored by means of fsarchiver) my jaunty desktop onto a pure GPT disk. Yes, it's possible to have only an EFI protective entry of type EE in MBR that spans whole disk, without any "hybrid" entries and still be able to boot Linux.

First of all, there has to be a so called "GPT BIOS boot partiton", i.e. non-filesystem GPT partition:

[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)


```

Partition GUID code: 21686148-6449-6E6F-744E-656564454649 (BIOS boot partition)

```

It's code is EF02, and it's GUID stands in hex for "Hah!IdontneedEFI" :)))
It could be very tiny, just 62 sectors as is the size of VBR but you can set any bigger size you like. Parted flag to create it is bios_grub. 

I'd rather recommed to use gdisk for further manipulation (it compiles on AMD 64 without a glitch, just warns of incompatible int types) because GNU Parted wipes MBR boot code when it deals with EFI protective MBR (it should according to standards, but not on BIOS machines!)

GRUB embeds into this small space, I just chrooted into my restored desktop and ran 
```

grub-install /dev/sdb

```

It works! You can in theory boot disk that's bigger than 2TB and have 128 partitions that don't rely on disk geometry and may have arbitrary sizes in sectors.

So I tried to add FreeBSD installation to it in a similar manner. Since I was using GRUB I didn't like the idea of having equivalent to "Hah!IdontneedEFI" tiny BSD GPT bios boot partition (which embeds BSD second stage loader) but tried to load /boot/loader directly with GRUB 2.

After restoration I was dropped to loader prompt and it warned me that no file on "/" could be read.

I know that you must specify root (hd0,6) as for example in my setup before calling freebsd (hd0,6)/boot/loader so that loader would set loaddev and currdev accordingly to faciliate further boot by kernel itself.

But this time it didn't boot. I had to enter set currdev=disk1p6 manually (GPT partitions are labeled "p" as opposite to MBR partitions which are called slices "s").

What GRUB passed to FreeBSD loader was disk1s6a (to look for BSD disklabel on MBR partition 6 - right number, after all - and not directly for UFS filesystem on GPT partition 6). It not only mistook p for s, but added a disklabel suffix, which normally is to be explicitly specified, (hd0,6a) then, if on MBR.

So, GRUB 2 handles GPT disks seamlessly for Linux, but confuses BSD loader, for the time being. Ah, forgot to mention, vga mode is horribly slow on GeForce 6 6200 AGP.

---

