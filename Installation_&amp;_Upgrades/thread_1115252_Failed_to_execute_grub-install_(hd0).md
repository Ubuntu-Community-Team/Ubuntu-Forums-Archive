---
title: "Failed to execute grub-install (hd0)"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by daigu on 2009-04-03
This post was first titled "Failed to execute grub-install (hd0)", but the issue has evolved since yesterday.

Preconditions: assembled custom system with "CPU 920 2.66GHZ CORE I7 QUAD 8MB BOX", "Asus P6T DELUXE V2" cpu, "HDD 1.5TB SATA SEAGATE 32MB 7200RPM" harddisk, "Asus EAH4350 SILENT/DI/512MD2" gpu, and "LG BLU RAY BRANDER GGW-H20L" drive. No OS pre-installed; however the motherboard is equipped with Asus Express Gate, from what I understand a very lightweight Linux based OS (embedded in flash memory) which allows the use of email and internet.

I've burned "ubuntu-8.04.2-server-amd64.iso" and "ubuntu-8.10-server-amd64.iso" on CD-R (after checking the MD5), using InfraRecorder (4x speed for 8.04.2, max speed for 8.10).

My first attempt was the 8.10 iso. I could not complete this installation due to the fatal error: "Failed to execute grub-install (hd0)"

My second attempt was the 8.04.2 iso. I could not complete this installation due to the fatal error: "No common CD-ROM drive detected" (during "Detect and mount CD-ROM"). Note that 8.10 did manage to find the CD-ROM.

When I start my computer, I see the message "No hard disk is detected" flashing over my screen. I don't know whether this is because Asus Express Gate cannot access the HDD (better said, it's not supposed to be able to access it), because the HDD is too big, or because of a technical error (I've contacted my supplier to rule out this last option).

I'll try the 8.10 iso again and write down every step along the way.

I do hope someone on this forum can help me. If you need a log file, kindly let me know how to create one. I'm a Linux newbie. Alt+F2 to open up the terminal?

---

### Post by daigu on 2009-04-04
Some background information on the ubuntu-8.10-server-amd64.iso installation:

Marvell 88SE61xx Adapter - BIOS Version 1.1.0.L72a
Initializing.

Adapter 1
Disks Information:
No hard disk is detected! (funny that, later on it spots the 1.5 TB ATA ST31500341AS dead on)

unable to enumerate usb device... (too fast to record the entire message)

Installation steps: (listing the warnings/errors only)

* Configure the network
Your system has multiple network interfaces. Choose the one to use as the primary network interface during the installation. If possible, the first connected network interface found has been selected.
Primary network interface:
- eth0: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Etherne
- eth1: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Etherne

* Configure the network
Network autoconfiguration failed
Your network is probably not using the DHCP protocol. Alternatively, the DHCP server may be slow or some network hardware is not working properly.

* Partition disks
Note that all the data on the disk you select will be erased, but not before you have confirmed that you really want to make the changes.
Select disk to partition:
- SCSI2 (0,0,0) (sda) - 1.5 TB ATA ST31500341AS
The selected device already contains the following LVM logical volumes, volume group and physical volumes which are about to be removed:
- Logical volume(s) to be removed: root, swap_1
- Volume group(s) to be removed: Satori
- Physical volume(s) to be removed: /dev/sda1
Note that this will also permanently erase any data currently on the logical volumes.

Yadda yadda...

The partition tables of the following devices are changed:
- SCSI2 (0,0,0) (sda)
The following partitions are going to be formatted:
- partition #5 of SCSI2 (0,0,0) (sda) as ext3

Yadda yadda...

The partition tables of the following devices are changed:
- LVM VG Satori, LV root
- LVM VG Satori, LV swap_1
The following partitions are going to be formatted:
- LVM VG Satori, LV root as ext3
- LVM VG Satori, LV swap_1 as swap
- partition #5 of SCSI2 (0,0,0) (sda) as ext3

* Install the GRUB boot loader on a hard disk
Installation step failed
An installation step failed. You can try to run the failing item again from the menu, or skip it and choose something else. The failing step is: Install the GRUB boot loader on a hard disk
You will need to boot manually with the /vmlinuz kernel on partition /dev/mapper/Satori-root and root=/dev/mapper/Satori-root passed as a kernel argument.

---

### Post by daigu on 2009-04-05
Since 8.10 did recognize the cd-rom, I figured I could just swap the CDs when 8.04.2 was looking for the cd-rom drivers, but the setup only allows to get these files from a disk? That's slightly inconvenient since I only have a cd drive. Ubuntu is very specific about needing a disk drive. Seems a bit old fashioned.

I'm replying to my own post because who knows, if I ever solve this problem it will make for a nice reference.

---

### Post by daigu on 2009-04-05
Trying to install ubuntu-8.04.2-desktop-amd64.iso, I end up with BusyBox v1.1.3 (Debian 1.1.3-5ubuntu12) Built-in shell (ash)
(intramfs)

Already noticed a very lengthy thread on this, with numerous possible solutions.

It's quite ironic that Ubuntu is going to be the reason for me to buy Windows Vista. Installing an OS on my computer should be simple as I only have one harddisk, I don't have an OS already installed, and all I want is a native installation.

My guess would be that the problem lies with the "Adapter 1
Disks Information: No hard disk is detected!" issue.

---

### Post by chappersuf on 2009-04-06
I too have a setup based on the Asus P6T Deluxe V2, i7 920, 12GB RAM, 4TB HDD (4x1TB WD EADS), Sapphire 4850x2, using everything else "onboard"

The best thing to do is install from one of the 8.10 alternate images: [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

After setting up with logical volumes on top of RAID (1 for boot partitions; 5 for everything else), I cannot install GRUB successfully.  The reason for using the 'Alternate' is because it has support for RAID and LVM, but most importantly, it will try installing LILO once GRUB install fails.

I've spent much time trying to get GRUB installed on the HDDs under the /boot LV on PV on RAID1, but haven't conquered it yet.  I prefer GRUB, but LILO works perfectly and installed automatically after GRUB failed during the install.

If I figure out how to successfully boot from GRUB, I'll post back here.

---

### Post by daigu on 2009-04-06
The solution (according to the Dutchies on ubuntu-nl), is NOT to use LVM. This solution worked fine for me with the ubuntu-8.10-server-amd64.iso. I still get the message that the hard disk is not found, but at the end of the day, Ubuntu installed properly (as far as I can tell).

The solution for my "No common CD-ROM drive detected" problem with ubuntu-8.04.2-server-amd64.iso might be to change some BIOS setting from SATA to ahci, but I haven't tried that.

Not sure if I should close this thread, since you still have an issue?

---

### Post by macracan on 2009-04-09
I too have problems installing this 8.10 (kubuntu dvd, 64bits). I fails with "Failed to execute grub-install (hd0)" at 94%.

This is my first time installing Ubuntu. I came to it because Fedora 10 is unstable. Well, Ubuntu can't even install... :(

I'm not using any exotic (RAID/LVM) partition magic. I have a separate partition for /boot, one for /home both of which I want to preserve from my alternate OS (Fedora 10). I have a whole partition / dedicated for Ubuntu which I did format. In fact here are the details
/dev/sda1  100MB  /boot  not-format (preserve from prior OS installs, but has about 60MB free)
/dev/sda2  4G swap 
/dev/sda3  lotsofGb /home not-format (preserve from prior OS installs)
/dev/sda4  extendedpartition
  /dev/sda5  10G / for Fedora 10 marked as not used during the install
  /dev/sda6  10G / for Ubuntu 8.10 (intended). formatted during install

I think it is absolutely ridiculous that grub cannot install. As it seems this is an OLD issue, present in Ubuntu 7.10 too with no resolution yet. Come on, guys, it is 21st century, can't we get an OS installed???

It seems I'm going back to Fedora. Better unstable than not at all...
If a resolution to this install does present itself, I'd be very glad to give Ubuntu another try.

---

### Post by daigu on 2009-04-09
My installation halted at 50%. But without LVM it worked just fine. Currently I'm running the desktop version though.

In some other posts it's mentioned that the CD might have errors. Did you check the md5 and burn on low speed?

The "Adapter 1 Disks Information: No hard disk is detected!" issue was unrelated to Ubuntu.

I'm also a tad disappointed with Ubuntu (probably had too high expectations), and it reminds me of my first BeOS experience. But it's either this or Vista, so...

---

