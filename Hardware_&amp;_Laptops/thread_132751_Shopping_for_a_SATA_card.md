---
title: "Shopping for a SATA card"
date: 2006-02-18
forum: Hardware &amp; Laptops
---

### Post by talz13 on 2006-02-18
I'm looking for a PCI SATA controller for my ubuntu system, as any HD that I buy from now on is going to be SATA.  I'm looking at the 400gb WD SATA drive here:

[http://www.newegg.com/Product/Product.asp?Item=N82E16822144424](http://www.newegg.com/Product/Product.asp?Item=N82E16822144424)

and wanted to know what specific SATA cards are known to play well with ubuntu.  A two port card would suffice, but something that has more than that would be appreciated (something with 4 or more ports mabye?), since I'll probably be adding another 400 in the near future.

I'm currently using LVM to span my disks together, and would like to know if there's any problem with moving my current setup to the new drive (since the single new drive will be almost twice as big as both the drives it's filling in for).

---

### Post by Orpheus- on 2006-02-19
I've just bought a Promise SATA300 TX4 card (the non-RAID variety), which has a GPL'd driver and works fine with my Ubuntu setup. Don't expect hotplug to work though.

Edit: This one
[http://www.newegg.com/Product/Product.asp?Item=N82E16816102062]("http://www.newegg.com/Product/Product.asp?Item=N82E16816102062")

---

### Post by talz13 on 2006-02-19
[QUOTE=Orpheus-]I've just bought a Promise SATA300 TX4 card (the non-RAID variety), which has a GPL'd driver and works fine with my Ubuntu setup. Don't expect hotplug to work though.

Edit: This one
[http://www.newegg.com/Product/Product.asp?Item=N82E16816102062]("http://www.newegg.com/Product/Product.asp?Item=N82E16816102062")[/QUOTE]

Can you clarify what you mean about hotplug?  Do you mean hotplug doesn't detect and configure the card, and I'd have to install it myself?  Or something about configuring the drives running off it?

Also, could you point me to some info about the GPL driver for it?  I'd like to check it out so I can be ready if I purchase this card.

---

### Post by jimmer on 2006-02-19
I also have the Promise SATA300 TX4 card, it is not supported out of the box. You need the GPL drivers found on promise.com and compile to the current kernel 2.6.12. See keebler411 post (General - HOWTO: Install Promise sata controllers using source). I am new to linux and still haven't been successful in compiling the kernel with promise drivers. However, this card is supported in kernel 2.6.14. Come April, Dapper Drake stable will be released. I believe the kernel in Alpha 4 is 2.6.15. I am downloading and will test to see if it identifies this controller. If anyone has any tips in how to get this card to work in Breezy I would be most appreciative. This is otherwise a good card works with my old Asus 3B-F MB and finds all my Seagate 400GB drives in its bios.

---

### Post by Orpheus- on 2006-02-20
[QUOTE=talz13]Can you clarify what you mean about hotplug?  Do you mean hotplug doesn't detect and configure the card, and I'd have to install it myself?  Or something about configuring the drives running off it?

Also, could you point me to some info about the GPL driver for it?  I'd like to check it out so I can be ready if I purchase this card.[/QUOTE]

Sorry, should have been more clear. By hotplug, I mean the ability (in theory) to remove and install a SATA drive with the computer running. Currently, doing so under Linux leads to problems. If you don't need that particular feature then there's no issues.

As for using the drive, I also followed [this HOWTO]("http://ubuntuforums.org/showthread.php?t=126199"). However, I did things slightly differently. For this to work, you must have an existing Ubuntu installation and add the SATA drive as an extra drive. Also, if you update the kernel to a new major version you will no longer be able to see the drive. I decided this wasn't a problem for me because the next kernel upgrade I do will be when Dapper Drake is released, which supports the card out of the box.

Here's the steps I followed (Breezy Badger 5.10, i386). Some of these are taken from the link above (in other words, give keebler411 the credit for this). You'll need to be root or use sudo in front of just about every command.

1) Install the card and drives in the computer. Verify that the card detects the drives and shows a message to this effect on boot.

2) Install the following packages:
apt-get install kernel-source-2.6.12
apt-get install build-essential
apt-get install kernel-package
apt-get install gcc
apt-get install gcc-3.4
apt-get install libncurses5
apt-get install libncurses5-dev
apt-get install libqt3-mt-dev

3) Unpack the kernel source:
cd /usr/src
tar --bzip2 -xvf linux-source-2.6.12.tar.bz2
ln -s linux-source-2.6.12 linux

4) Download the appropriate source code file from Promise for your controller to /usr/src and unpack it. Mine was called 2_sataii150-300-tx-series-linux2.6-src-x86_v1.01.0.20.tar.gz. It unpacks to ut_mod.

cd /usr/src
tar -zxvf 2_sataii150-300-tx-series-linux2.6-src-x86_v1.01.0.20.tar.gz

5) Compile, but do not install the kernel.

cd /usr/src/linux
make clean
cp /boot/config.`uname -r` .config
make oldconfig
make bzImage
make modules

6) You don't need to install the kernel, because you've just compiled an identical kernel to what's installed already. This allows the driver to pick up the information it needs to compile properly. Now compile the driver.

cd /usr/src/ut_mod
less README

7) All the information you need is in the README file. Read it (seriously). Here's the short version.

make clean
make DRIVER_SRC_DIR=`pwd`
cp ulsata2.ko /lib/modules/`uname -r`/kernel/drivers/scsi/
depmod -a
modprobe ulsata2.ko

8) At this point you should have access to /dev/sdX and be able to mount the drives. Check dmesg to see if anything looks odd. If it worked, get the module to load on boot.

cd /etc/mkinitramfs/modules
yourfavouriteeditor modules
  -- add ulsata2 to the end of this file, on a line of its own.
cd /boot
mkinitramfs -o initrd.img-`uname -r`

*** I'm not sure if this is a good idea. It overwrites the default initrd image, which is probably unwise. A better idea would be to make a new version and point grub to it. However, it works for me, and it's really a stopgap until I upgrade to 6.04 in April. ***

9) Fiddle around in fstab and so on.

---

