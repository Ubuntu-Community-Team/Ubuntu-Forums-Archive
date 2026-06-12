---
title: "Rocket Raid Card Driver Problems"
date: 2006-08-03
forum: Hardware &amp; Laptops
---

### Post by CharlieM on 2006-08-03
[FONT="Verdana"][SIZE="2"]I am fairly new to Ubuntu although I have toyed with other distros for the last 5 years or so. I am trying to migrate my personal server from FreeBSD to Ubuntu Server (for Myth TV mostly). 

My server has a Rocket Raid 1820 SATA card in it. On FreeBSD the drivers were integrated in to the OS unfortunately on Linux they aren’t. There are drivers for various other distros on the manufactures web site but not for Ubuntu. They provide "open source" drivers for other distros, these are a wrapper on a precompiled library so you can link against your own kernel. (see their web site [http://www.highpoint-tech.com/USA/bios_rr1820a.htm#LinuxDrivers](http://www.highpoint-tech.com/USA/bios_rr1820a.htm#LinuxDrivers))

I installed the kernel headers and build tools then used the drivers make file to build and install them. The read me then tells you to run:

modprobe hptmv

This loads the newly installed raid driver. This even using the verbose switch loads without errors. It appears to be running under lsmod although there is no sign of any new drives under /dev.

 About five minutes after running the mode probe command the RAID alarm on the card sounds (sounds like a lorry reversing siren, gave me a massive scare the first time). Then when I reboot the RAID BIOS complains about drive one now being corrupt and wants to rebuild the array (its currently configured as RAID 5) , luckily there is no unbacked up data on the array.

During the boot process with and with out the drivers installed it spends about 5 minutes on the loading hardware drivers stage. At about 1 minute intervals it prints the following on the screen

[42949473, 82000] ata1: failed to set xfermode, disabled

This is repeated another 4 times (ata1 – ata5). I assume some how the kernel has managed to access each of the disks on the raid card (there are 5). Could this be what causing problems for Manufactures drivers? It does take nearly five minutes before the raid alarm goes off.

I tried using [http://kmuto.jp/debian/hcl/](http://kmuto.jp/debian/hcl/) to look up the compatibility of my hardware. The only mention I can find of the raid card is the below entry. 

11ab5081, YesMarvell Technology Group Ltd. MV88SX5081 8-port SATA I PCI-X Controller, sata_mv

I checked and the sata_mv driver is loaded. Is this driver letting the OS access the raid cards drives. Is there some why to disable this and make the kernel use the Manufactures driver instead. When the manufactures driver is installed it still chooses the sata_mv at boot time.

I would be grateful for any help or suggestions anyone can give.

Charlie[/SIZE][/FONT]

---

### Post by CharlieM on 2006-08-04
I have done a bit of diging. I read the dmesg output and deccided it was probably the sata_mv driver that was interfering when I load the Manufactures driver. 

So I managed to remove the modual by removing it from the kernel/drivers/scsi/ folder then recrated the boot image. That stopped all the dmesg error messages and the long boot time. 

I then used modprobe to load the manufacturies driver. This time no RAID alarm or drive coruption. I installed the managment CLI and that appears to be working. Its currently rescreating the array.

The only thing I don't know is where the array should appear in /dev hopefully it will be obvious after the array has been initialised. Problem is the array is nearly a terabyte and it takes serveral hours to rezero so I will have to wait and see. 

I am not an expert in Linux and I would think there is probably a better way of disabling the sata_mv driver although it does appear to work.

---

### Post by hkgonra on 2006-10-02
I would love some info on this as well. I have the Rocket Raid 1820 as well and would love to do a clean install of ubuntu on it.

---

### Post by CharlieM on 2007-01-17
Booting from the RAID array is more complicated, I think. My home server now has 6 250 gig SATA hds and one old 40gig IDE hd I had lieing around. The OS and home partions are stored on the 40 gig HD the important data is on the RAID array. 

As I understand it, to boot off an array on the RAID card you first need to patch the boot CD you use to do the install of the OS. After all how can the installer work if it doesn't know how to write to the destination drive. I have only seen instructions to do that on debian not ubuntu although I am sure its a similar proccess.

I have been doing it the other way round, installing the OS then modifing the installed initrd image to contain the RAID drivers and more importantly remove the conflicting one. 

I have just upgraded to Edgy Server and needed this thread to remind me how I got the drivers working. 

Charlie

---

