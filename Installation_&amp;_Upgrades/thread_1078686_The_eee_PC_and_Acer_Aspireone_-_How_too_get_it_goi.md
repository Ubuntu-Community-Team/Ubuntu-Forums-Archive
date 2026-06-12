---
title: "The eee PC and Acer Aspireone - How too get it going"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by J_dillinger on 2009-02-23
With the introduction of the eee PC and the Aspireone I was in love...  Originally I had to have the Asus, but with the great deal Walmart offered on Black Friday (yeah, I know but I bought the acer at wallyworld) I bought an Aspireone as well.  Let me start out with the good, bad, and the ugly of both boxes.

The Asus eee PC 1000HD weighing in at 900 MHz Intel Atom with a 120 gig hard drive supporting USB/SD card boot.  The eee PC came with Windows XP installed and since I have  installed Ubuntu 8.10 and run Backtrack 3 off of an SD Card.  3 USB port (1 on the left and 2 on the right side of the box) and 1 SD card slot.  Three Ubuntu packages exist to improve support for the eee PC
eee-applet
eee-control
eeepc-acpi-scripts

The Acer Aspireone Weighs in with a 1.6 GHz Intel Atom with a 160 gig hard drive supporting USB boot.  The Aspireone came with Windows XP installed and since I have  installed Ubuntu 8.10 and run Backtrack 3 off of an SD Card.  3 USB port (1 on the left and 2 on the right side of the box) and 2 SD card slots (one is designed to act as additional Hard Drive space to move from box to box).

The wireless drivers for both boxes can be installed with the following method

wget [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz)
sudo apt-get install build-essential linux-headers-$(uname -r)
tar -xzf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6*/
make
sudo make install
sudo modprobe ath_pci

You will probably also have to edit /etc/modules with the following...
sudo nano /etc/modules

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ath_pci

I also had no problem installing the codecs for totem player and gtotem (I recomend the good bad and the ugly and using decrypted ISO to play movies)

I would like to thank the member who posted the information about the ath_pci wifi on ubuntu forums for the information listed here @ 
Ubuntu Documentation > Community Documentation > AspireOne 
also I would reccomend checking synaptic package manager for the eee PC because special modules have been added to support the eee PC

remaster.sys also works great to remaster iso files for future installation and build remastered updated usb boot drives

The following third party repositories were added to download the packages...
[http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository)
[http://www.linuxmint.com/repository](http://www.linuxmint.com/repository)
[http://www.array.org/ubuntu](http://www.array.org/ubuntu)     (eee PC)


Both of these computers are great solutions for compact computing and have the power to support just about all applications for programming and network or tech support.  As a field tech I love both of these systems and would recomend either of them to anybody.  Unfortunately, the Acer has a faster processor and larger hard drive.

---

### Post by kyphi on 2009-02-23
Just for your information:

The Intel Atom processor runs at 1.6 GHz - the Intel Dothan processor runs at 900 MHz.

Specifications often differ from one country to the next. 

Both my eee pcs (1000H and 701 - the 1000H does have the Atom processor) run the Ubuntu netbook remix which does not need any additional tweaking or installations.

Fantastic machines - small enough to fit into a lady's handbag but fully functional.

---

