---
title: "XP can't see hard disk after Ubuntu install"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by johnp11 on 2009-01-14
I just installed Ubuntu into existing free space in an existing extended partition on my 1st hard drive. Ubuntu works OK, but the previous installations of Windows XP don't seem to recognize the hard disk anymore. XP will start to boot, then die with a STOP 7B, which is what happens when it can't read the boot drive. There are two XP installations on that drive (sda1 and sda5) and neither one of them will boot.

Everything looks OK under Ubuntu, I'm not seeing any errors reported by fdisk or testdisk. If I boot the XP install CD, it says "setup cannot access this disk" under my 1st hard disk, and it shows the size as 476938 which is incorrect. I have an identical 2nd drive and it's size is listed correctly as 238473, and XP setup can see the existing partition on that drive.

I am able to mount the old partitions on my 1st hard drive under Ubuntu and everything still seems to be there, but for some reason XP can't read it. Any ideas?

Here's my fdisk -l and menu.lst:

```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d981d98

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6527    52428096    7  HPFS/NTFS
/dev/sda2            6528       30401   191767905    f  W95 Ext'd (LBA)
/dev/sda5            6528       12902    51207156    7  HPFS/NTFS
/dev/sda6           12903       30401   140560686   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x430c430b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

```

```

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		f73c73a4-2438-4914-972f-805af30a8a71
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=f73c73a4-2438-4914-972f-805af30a8a71 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		f73c73a4-2438-4914-972f-805af30a8a71
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=f73c73a4-2438-4914-972f-805af30a8a71 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f73c73a4-2438-4914-972f-805af30a8a71
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f73c73a4-2438-4914-972f-805af30a8a71 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f73c73a4-2438-4914-972f-805af30a8a71
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f73c73a4-2438-4914-972f-805af30a8a71 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		f73c73a4-2438-4914-972f-805af30a8a71
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by logos34 on 2009-01-14
are these sata or ide hard disks?

sudo lshw -C disk

---

### Post by johnp11 on 2009-01-14
They're SATA drives, running in AHCI mode.

```

  *-disk:0
       description: ATA Disk
       product: ST3250310NS
       vendor: Seagate
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: SN04
       serial: 9SF04BAL
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=1d981d98
  *-disk:1
       description: ATA Disk
       product: ST3250310NS
       vendor: Seagate
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/sdb
       version: SN04
       serial: 9SF04CRZ
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=430c430b

```

---

### Post by logos34 on 2009-01-14
> **johnp11 said:**
> They're SATA drives, running in AHCI mode.

That's what I figured. It appears XP was installed in IDE compatibilty mode (aka 'emulation' or 'legacy'), but linux is running in AHCI mode. (Linux natively supports AHCI, XP doesn't--requires you to manually load the sata drivers from floppy before installation).

Check by changing the sata setting to ide.  If XP boots ok that's the proof

So probably the easiest way to fix this is to reinstall ubuntu, but make sure the bios is set for compatibility mode. (I wonder how it got changed).

The harder way is to reinstall windows and insert the drivers beforehand with F6 key, or else slipstream the drivers into a new custom XP install CD image with nLite.

ADD: you could also do nothing, but you'll have to go into the Bios before you boot the other OS each time to change the Sata mode.

---

### Post by johnp11 on 2009-01-15
> **logos34 said:**
> That's what I figured. It appears XP was installed in IDE compatibilty mode (aka 'emulation' or 'legacy'), but linux is running in AHCI mode. (Linux natively supports AHCI, XP doesn't--requires you to manually load the sata drivers from floppy before installation).

Check by changing the sata setting to ide.  If XP boots ok that's the proof

So probably the easiest way to fix this is to reinstall ubuntu, but make sure the bios is set for compatibility mode. (I wonder how it got changed).

The harder way is to reinstall windows and insert the drivers beforehand with F6 key, or else slipstream the drivers into a new custom XP install CD image with nLite.

ADD: you could also do nothing, but you'll have to go into the Bios before you boot the other OS each time to change the Sata mode.

THANK YOU, that worked. The weird thing is that XP was installed with AHCI drivers. It wouldn't have even seen the controller if I hadn't provided them during the install (I made an nLite CD). And both drives are on the same controller, but XP could see the 2nd one but not the first. It's like it just forgot that the 1st drive was on an AHCI controller somehow. I switched the controller to PATA mode, and now XP boots, but prompts me to install drivers for my IDE controller. I'm afraid to touch anything because I need to get some work done right now.

I don't know what this had to do with installing Ubuntu, if anything, but it sure would be a strange coincidence.

Thanks again!

---

### Post by logos34 on 2009-01-15
yeah, weird is right (that's windoze for you), but glad it's booting now.

good luck

---

