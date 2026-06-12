---
title: "Installing on onboard ide hdd with sil680 raid present"
date: 2005-12-28
forum: Installation &amp; Upgrades
---

### Post by deunan on 2005-12-28
Actually, I just want to describe my installation process..

I got a PC with 4 IDE HDDs and 2 Opticals (DVD-ROM and CDRW).  Naturally, I want to connect all these HDDs and the Opticals as well.  I'm using the RAID card as an ordinary extra IDE ports, no RAID stuff whatsoever (I need the space  ;-)

The HDD arrangement is as follows -

Primary Master - 40GB HDD
Primary Slave - 80GB HDD

Secondary Master - DVD-ROM
Secondary Slave - CDRW

Sil680 RAID PCI
Primary Master - 40GB HDD
Primary Slave - 40GB HDD


Now, when all the above is connected, when I install Ubuntu onto Primary Master HDD, it detects everything normally, but when it comes to partitioning, Primary Master and Slave are both detected as "hde" and "hdf"..  Grubs then assigns the bootup hdd as HD(2,0)..  The first reboot, Grub cannot find the Primary Master HDD, when I fix the HD(2,0) to HD(0,0), it boots..  But when it wants to mount the filesystem, it says it cannot find "/dev/hde1"..

I tried disconnecting the 2 HDDs from the Sil680 RAID PCI card (by disconnecting the power supply wires), this time grub detects the Primary Master HDD and assign it properly to HD(0,0)..  But previously the partitioner still detect it as "hde"..  Upon bootup, grub works nicely, but filesystem loading fails as before, unable to detect "/dev/hde1"..

The finally working method I tried is that I pulled out the Sil680 RAID PCI card out of the system and install ubuntu normally.  Partitioner detect Primary Master as "hda" and grubs assigns it as HD(0,0)..  Later, when ubuntu goes into process of rebooting before continuing the installation, I switch-off the PC and plug-in back the PCI RAID card into it.  The PC boots up nicely, continuing the installation, and detects all the HDDs normally..

Primary Master - hda
Primary Slave - hdb
Secondary Master - hdc
Secondary Slave - hdd

Raid Primary Master - hde
Raid Primary Slave - hdf

The strange thing is that, with the RAID card plugged in, ubuntu mistakenly detects the RAID card ports as the first four ports in the system and the onboard IDE ports after that.  But when ubuntu reboots after installation process, it detects the onboard IDE ports as the first 4 and RAID card IDE ports after that.

Hope this info is useful somehow..

---

