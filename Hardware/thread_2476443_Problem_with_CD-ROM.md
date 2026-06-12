---
title: "Problem with CD-ROM"
date: 2022-06-26
forum: Hardware
---

### Post by gale85 on 2022-06-26
I have a problem with the CD-ROM in Ubuntu 22.04 is by no means visible. When I try to boot a bootable disk then it works without a problem which means the problem is up to the system

---

### Post by TheFu on 2022-06-27
How are you mounting it?  Please show the fstab entry or mount command used.

---

### Post by gale85 on 2022-06-27
I did not mount the CD-ROM in Ubuntu at all 22.04 I said it already works when the system needs to be booted from the disk and when it enters Ubuntu then only the eject and eject -t commands work but it will not show me the contents of a disk

---

### Post by TheFu on 2022-06-27
A file system has to be mounted to be accessed.  If you don't mount it, forgetabout it.  On some systems, there is a dæmon that will try to automatically mount file systems. Sometimes that automatic method fails and we need to help it.  My questions above are trying to gain the knowledge for whether we can help it or not.

Is there a device named for the cdrom?  It would normally be named /dev/sr0, but there could be other names depending on the cdrom driver used.  
```
$ lshw -C storage 
```
is another way to see if the OS knows about the cdrom/dvd drive.

---

### Post by ajgreeny on 2022-06-27
I don't know the gnome default version of Ubuntu but when using Xubuntu there are settings for ***Removable Drives and Media*** where you can choose what happens when you insert a CD or DVD.

Have a look in the settings for Ubuntu and I suspect there may be something similar which will allow the disks to be auto-mounted when detected in the drive.
This, of course assumes the drive is working as it should; they do have a limited life and my Desktop CD/DVD drive stopped working some time ago and I haven't bothered to replace it as I simply don't use CDs or DVDs any more though I do still have a laptop with a working drive which allows me to rip music or movies if I need to.

---

### Post by gale85 on 2022-06-27
lshw -C storage
```

WARNING: you should run this program as super-user.
  *-sata                    
       description: SATA controller
       product: JMB363 SATA/IDE Controller
       vendor: JMicron Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: sata ahci_1.0 bus_master cap_list
       configuration: driver=ahci latency=0
       resources: irq:19 memory:f9000000-f9001fff
  *-ide
       description: IDE interface
       product: JMB363 SATA/IDE Controller
       vendor: JMicron Technology Corp.
       physical id: 0.1
       bus info: pci@0000:03:00.1
       logical name: scsi4
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: ide pci_native_mode bus_master cap_list emulated
       configuration: driver=pata_jmicron latency=0
       resources: irq:16 ioport:c000(size=8) ioport:c100(size=4) ioport:c200(size=8) ioport:c300(size=4) ioport:c400(size=16)
  *-pnp00:02
       product: PnP device PNP0700
       physical id: 2
       capabilities: pnp
  *-ide:0
       description: IDE interface
       product: 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode]
       vendor: Intel Corporation
       physical id: 1f.2
       bus info: pci@0000:00:1f.2
       version: 02
       width: 32 bits
       clock: 66MHz
       capabilities: ide isa_compat_mode pci_native_mode bus_master cap_list
       configuration: driver=ata_piix latency=0
       resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16) ioport:fc00(size=16)
  *-ide:1
       description: IDE interface
       product: 82801I (ICH9 Family) 2 port SATA Controller [IDE mode]
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 02
       width: 32 bits
       clock: 66MHz
       capabilities: ide pci_native_mode bus_master cap_list
       configuration: driver=ata_piix latency=0
       resources: irq:19 ioport:e700(size=8) ioport:e800(size=4) ioport:e900(size=8) ioport:ea00(size=4) ioport:eb00(size=16) ioport:ec00(size=16)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```
sudo lshw -C storage
```

  *-sata                    
       description: SATA controller
       product: JMB363 SATA/IDE Controller
       vendor: JMicron Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: sata pm pciexpress ahci_1.0 bus_master cap_list
       configuration: driver=ahci latency=0
       resources: irq:19 memory:f9000000-f9001fff
  *-ide
       description: IDE interface
       product: JMB363 SATA/IDE Controller
       vendor: JMicron Technology Corp.
       physical id: 0.1
       bus info: pci@0000:03:00.1
       logical name: scsi4
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: ide pm pci_native_mode bus_master cap_list emulated
       configuration: driver=pata_jmicron latency=0
       resources: irq:16 ioport:c000(size=8) ioport:c100(size=4) ioport:c200(size=8) ioport:c300(size=4) ioport:c400(size=16)
  *-pnp00:02
       product: PnP device PNP0700
       physical id: 2
       capabilities: pnp
  *-ide:0
       description: IDE interface
       product: 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode]
       vendor: Intel Corporation
       physical id: 1f.2
       bus info: pci@0000:00:1f.2
       logical name: scsi0
       version: 02
       width: 32 bits
       clock: 66MHz
       capabilities: ide pm isa_compat_mode pci_native_mode bus_master cap_list emulated
       configuration: driver=ata_piix latency=0
       resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16) ioport:fc00(size=16)
  *-ide:1
       description: IDE interface
       product: 82801I (ICH9 Family) 2 port SATA Controller [IDE mode]
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 02
       width: 32 bits
       clock: 66MHz
       capabilities: ide pm pci_native_mode bus_master cap_list
       configuration: driver=ata_piix latency=0
       resources: irq:19 ioport:e700(size=8) ioport:e800(size=4) ioport:e900(size=8) ioport:ea00(size=4) ioport:eb00(size=16) ioport:ec00(size=16)

```

---

### Post by TheFu on 2022-06-28
I haven't seen an IDE device in about a decade. There should be a device name if there is a disc inserted.  Are you seeing any devices with symbolic links from /dev/dvd or /dev/cdrom?

I vaguely remember some changes to the IDE driver. Think the BIOS has to be set to use AHCI for the last few years for IDE devices to perform better.  I know there has been discussions on the kernel email list about removing IDE support. [https://www.phoronix.com/scan.php?page=news_item&px=Linux-Drop-Legacy-IDE-2021](https://www.phoronix.com/scan.php?page=news_item&px=Linux-Drop-Legacy-IDE-2021)
[https://www.tomshardware.com/news/linux-kernel-nixes-ide-support-in-the-latest-514-release-candidate](https://www.tomshardware.com/news/linux-kernel-nixes-ide-support-in-the-latest-514-release-candidate)  Looks like kernels 5.14 and later won't have IDE support.

> Linux founder Linus Torvalds recently posted an update on the Linux Kernel Mailing List announcing the arrival of Linux kernel version 5.14. Perhaps the biggest change is the removal of legacy support for Parallel ATA (PATA), also referred to as ATAm or IDE.

22.04 releases come with kernel version 5.15.x. I'm a little confused that this is working on any 22.04 version.  You can check the kernel version by running **uname -r**

My 20.04 box without any HWE updates uses 5.4.0-121-generic.

---

### Post by guiverc on 2022-06-28
I just inserted a (*random*) 'software disc for Epson Stylus 480 (1997)' in my *kinetic* system (*using Lubuntu/LXQt currently, but I'd expect the same response if I log with GNOME, Xfce etc..*) and I get asked if I want to *mount* the inserted *disc.* I say yes, and for me `pcmanfm-qt` opens with the files from the random  *disc* I picked are shown.

I am aware some desktops by default don't auto-mount as my *current* Lubuntu does; and that response can vary on release being used too (*Lubuntu didn't for some older releases too*), as I've need to `mount` them in the past.

FYI: Lubuntu 22.04 LTS (*and Ubuntu 22.04 LTS Desktop*) will boot from DVD media; that was QA-tested, but it's **very** slow  (*I'd not recommend it; use USB media!*).

I don't need to do anything unusual to read CD/DVDs, and haven't yet for any *daily* ISOs created by Ubuntu (*including flavors which I use more regularly*). 

My box is OLD (*2009 dell desktop*), but most *optical media/drives *are **OLD** now too, so *I'd check the drive actually works*.  My last 5 writes of *DVDs* have resulted in 3 drives needing to be replaced, as the drives themselves had failed (*each write after install worked; then on subsequent write a failure again; not all the same box so it's not related to other hardware [PSU etc] in box too..*). I'm not installing new drives, just grabbing a working one from a stack of *tested* replacements pulled from *prior-**recycled* boxes (*which accounts maybe for my high-failure rate*), **but **with my experience I'd **check** you still have a functioning drive.

I've had to do nothing to have CD/DVDs recognized & work in all *current desktop* releases of Ubuntu *where the drive itself functions*.  I can't say which (*DE/release*) will auto-mount (*I can't recall*); as my testing was only that it worked.

---

### Post by gale85 on 2022-06-28
All right, what do you suggest I do? I can't start the installation via USB, so this is the only solution for me via CD-ROM, more precisely DVD-ROM, I don't know what to do anymore, my computer is completely in disarray. I thought it was easier to just insert the disk and reinstall ubuntu 22.04 since something went completely wrong, so I thought it was easier to reinstall the system than to sort one by one. What is your opinion?

---

### Post by guiverc on 2022-06-28
You can re-install from DVD... that was tested & worked successfully (*much of the time**; there were a few cases were problems were encountered, but on re-try it worked*).  The installations done were all simple installs, not (*non-destructive & manually installed package add*) re-installs though.

Allow plenty of time, it can take an hour to fully boot a 22.04 ISO from DVD; as release does a scan of the installation media looking for issues, and in simple terms it does that on a file-by-file basis, rather than the whole of media. Optical media was designed to be read from start to end sequentially (as in playing music/video), not jumping around randomly reading small files spread all over the disks.  There is a *lp bug* to have this feature not run when slow media (such as DVD/CD, but also some cloud environments) is detected, but current ISOs do the scan. I'd suggest waiting for the scan to complete before install.

I know you can, what I like calling "*upgrade via re-install*" which can be used to fix packaging issues etc... (*where files aren't touched, and your manually installed packages will get auto-reinstalled*) but whilst I do that rather regularly (*in QA*), it was not tried with DVD media as it took so long, and DVD installs were *somewhat* *problematic* (*occasional issues, but if you repeated the step it was flawless; ie. inconsistent with timeout issues involved*).  They are possible however, it just may require a couple of installs to get it work, and a ***ton*** of patience.

Myself, I'd likely have the ISO written to other media if the machine already has `grub` installed & in control of booting, and have the ISO boot from other media & run from there. That was my preference when using an old thinkpad with no working (*bootable*) USB ports over using its DVD drive with media on it. I didn't install to the portion of the disk the ISO was being read from but to another partition, but that was mostly so I didn't have to re-setup the ISO boot process each time.  I'm aware of others who have used CF, SD-cards & other media to install from too as you can use anything your box will boot from, but I'd opt for disk if I can't use USB-flash media.

---

