---
title: "Ubuntu with Fibre Channel card and Arrays?"
date: 2005-04-05
forum: Hardware &amp; Laptops
---

### Post by Beebe on 2005-04-05
Hi

At work we currently have a Solaris system, this has a fibre channel card fitted.

We use this to connect to an array of 58 fibre channel drives to format and verify the disks. We do this by opening a console for each drive and typing format and drive location.

We have had nothing but problems with Solaris and was wondering if Ubuntu would work?

---

### Post by alastair on 2005-04-05
The Linux kernel supports a lot of FC HBA's e.g. Qlogic etc.

As long as the HBA is supported, there's no reason why not. But there's only one way to find out ...

---

### Post by danja on 2005-04-06
That's good to hear Beebe ;)

We'll have to look into trying it as a tester then...

---

### Post by brianfinley on 2005-04-25
[QUOTE=alastair]The Linux kernel supports a lot of FC HBA's e.g. Qlogic etc.

As long as the HBA is supported, there's no reason why not. But there's only one way to find out ...[/QUOTE]

For some reason, which I'd like to know, Ubuntu has omitted many of the qlogic drivers from their binary kernel.  The source appears to exist, but the standard kernel config methods don't indicate that they are available for inclusion when using the Ubuntu source.  (2.6.10 series ubuntu kernel).

Ubuntu, what gives?  I need the qla2300 driver and have had to compile and install my own kernel.  I'd really like to be able to use and promote ubuntu as is.

Cheers, -Brian

---

### Post by alastair on 2005-04-25
Driver support is often in a state of flux i.e. you can not expect kernel 2.6.X to be the /latest/ drivers available. If you need a later driver (perhaps not), you can check the QLogic web site or e.g.

[ftp://ftp.qlogic.com/outgoing/linux/](ftp://ftp.qlogic.com/outgoing/linux/)

Sometimes device support gets rolled up into a "generic" module (different name). 

However, you might be fine because there are drivers in 2.6.10 e.g.

root@muse:/home/alastair # uname -r
2.6.10-5-386

root@muse:/home/alastair # cat /boot/config-2.6.10-5-386 |grep QL
CONFIG_SCSI_QLOGIC_FAS=m
CONFIG_SCSI_QLOGIC_ISP=m
CONFIG_SCSI_QLOGIC_FC=m
CONFIG_SCSI_QLOGIC_FC_FIRMWARE=y
CONFIG_SCSI_QLOGIC_1280=m
CONFIG_SCSI_QLOGIC_1280_1040=y

Check that one of the modules shipped works :

qla1280.ko
qlogicfc.ko
qlogicisp.ko

Download and check the "linux-doc" package.

Even if you want or need to build a new driver, you should only need to build a module, not a complete kernel.

---

### Post by brianfinley on 2005-04-29
Unfortunately, those are not the drivers I need.  I need the qla2300 driver (CONFIG_SCSI_QLA2300).  Here are the relevant entries from a vanilla kernel from kernel.org that I had to compile myself to get support:

finley@bro3:/boot$ grep QLA config-2.6.11.7bef
CONFIG_SCSI_QLA2XXX=m
CONFIG_SCSI_QLA21XX=m
CONFIG_SCSI_QLA22XX=m
CONFIG_SCSI_QLA2300=m
CONFIG_SCSI_QLA2322=m
CONFIG_SCSI_QLA6312=m

And here is the same grep against the Ubuntu config file:

finley@bro3:/boot$ grep QLA config-2.6.10-5-386
finley@bro3:/boot$

You'll notice a distinct lack of option to configure the qla2300 driver. ;-)

Why _remove_ drivers from the kernel?

---

### Post by alastair on 2005-04-29
I don't know the deal here. I have used a QLogic card - but I had to use Redhat 8, for a specific kernel for a third-party proprietary driver (SAN stuff). What I do know is that some drivers, including QLogic, are often in a state of flux - drivers being coalesced sometimes, files changing.

You might want to download the Ubuntu 2.6.10 kernel source, and the Ubuntu patches, and check the differences.

I doubt it is an explicit decision to remove functionality on the part of the Ubuntu maintainers.

Anyway - good luck.

---

### Post by brianfinley on 2005-11-02
I see that the open source qlogic drivers are now included (Ie: not removed from the kernel) with Breezy.  Thanks guys!

---

### Post by sudirt on 2006-02-02
I am not sure if this is a super old post or not...yet if any of you guys are still on here I would love to hear of an update to the fibre channel drive tester. I am essentially doing something very similar. Perhaps we can talk more if I knew there was still activity from you.

Thanks
Sudirt

---

### Post by brianfinley on 2006-02-03
Recent Ubuntu kernels (Breezy) include the vanilla kernel driver.

If you want the most recent qlogic driver, try this:

#
# Created 2006.02.03, Brian Elliott Finley
#
URL=ftp://ftp.qlogic.com/outgoing/linux/beta/8.x/qla2xxx-src-v8.01.04b4.tar.bz2
TARBALL=`basename $URL`
KERNEL_VER=`uname -r`
cd /tmp
wget $URL
tar -xvjf $TARBALL && mv $TARBALL x-$TARBALL
cd qla2xxx-*
sudo apt-get install linux-headers-`uname -r` gcc-3.4
BUILDDIR=/lib/modules/${KERNEL_VER}/build
ls $BUILDDIR/    # just to verify
sudo make -C $BUILDDIR M=`pwd` clean
sudo make -C $BUILDDIR M=`pwd` modules
sudo install -d -m 755 -o root -g root /lib/modules/${KERNEL_VER}/kernel/drivers/scsi/qla2xxx/
sudo install -m 644 -o root -g root *.ko /lib/modules/${KERNEL_VER}/kernel/drivers/scsi/qla2xxx/
sudo depmod
sudo mkinitramfs -o /boot/initrd.img-`uname -r`

---

