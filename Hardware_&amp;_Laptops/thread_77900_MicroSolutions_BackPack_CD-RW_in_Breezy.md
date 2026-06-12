---
title: "MicroSolutions BackPack CD-R/W in Breezy"
date: 2005-10-17
forum: Hardware &amp; Laptops
---

### Post by jmb365 on 2005-10-17
Hi,

I have recently installed Breezy on a previously RH8 PC that was working fine with my MicroSolutions Parallel Port BackPack CD-R/W (Series 6).  After repeated attempts at trying to make it work on FC3, I gave up and decided to try Breezy.  This is my first experience of Ubuntu and I am impressed.  For those of you who want to connect this archaic external CD-R/W drive here is how to do it.  My script, which I stumbled upon after many RH8 tweaking days & nights are shown below.  It also works on Breezy!  All comment lines are included as possible fixes for your particular situation.  Make sure your BackPack is connected to the parallel port before booting and your BIOS setting for the parallel port is: PCSPP,TRISTATE,EPP

You can check the Parallel port setting by:
cat /proc/sys/dev/parport/parport0/modes

# Start here...

# modprobe parport		# Already maybe loaded
# modprobe parport_pc		# Already maybe loaded

modprobe paride

#
# The following 2 steps are not necessary on Breezy...
# 	mkdir /lib/modules/$(LINUX_VERSION)/misc
# 	cp /lib/modules/$(LINUX_VERSION)/kernel/drivers/block/paride/bpck6.o /lib/modules/2.4.20-20.8/misc/backpack.o

echo "Inserting the necessary modules..."
modprobe bpck6
modprobe pg		# For CD-R/W
modprobe cdrom
modprobe pcd		# For CD-R

dmesg | grep paride
# Look for: "paride: bpck6 registered as protocol 0"

# modprobe pcd drive0=0x378,1 drive1=0x3bc,1	# Example syntax
# To support such a wide range of devices PARIDE, the parallel port IDE subsystem, is actually structured in three parts.
# There is a base paride module which provides a registry and some common methods for accessing the parallel ports. 
# The second component is a set of high-level drivers for each of the different type of supported device:
# pd 	IDE disk
# pcd	ATAPI CD-ROM
# pf 	ATAPI disk
# pt 	ATAPI tape
# pg 	ATAPI generic devices

# The pg driver exists mainly to support parallel port ATAPI CD-R and CD-RW devices. 

#
# Run the commands below from a script 
# ====================================================================
echo "Running the commands of Check4CDDrives..."
test `whoami` = 'root' || echo "You must be root to execute the commands."
cdrecord -scanbus > /dev/null
if ! (pidof kerneld || test -f "/proc/sys/kernel/modprobe"); then
    echo "Neither kerneld nor kmod are running to automatically load modules".
fi
report_no_autoload() {
    echo "Ensure the module $1 is loaded automatically next time."
}
if test ! -f "/proc/scsi/scsi"; then
    report_no_autoload scsi_mod  &&  modprobe scsi_mod
fi
if ! grep "^........ sg_" /proc/ksyms > /dev/null; then
    report_no_autoload sg  &&  modprobe sg
fi
if ! grep "^........ sr_" /proc/ksyms > /dev/null; then
    report_no_autoload sr_mod  &&  modprobe sr_mod
fi
if ! grep "^........ loop_" /proc/ksyms > /dev/null; then
    report_no_autoload loop  &&  insmod loop
fi
if ! grep iso9660 /proc/filesystems > /dev/null; then
    report_no_autoload iso9660  &&  modprobe iso9660
fi
echo "The following is only needed for IDE/ATAPI CD-writers."
if ! grep ide-scsi /proc/ide/drivers > /dev/null; then
    report_no_autoload ide-scsi  &&  modprobe ide-scsi
fi
# ================================================================

# Now check if it is recognized:
cdrecord -scanbus

# Mount to an appropriate location after placing a CD in the drive
mkdir /mnt/backpack
mount -t iso9660 /dev/pcd0 /mnt/backpack
ls -al /mnt/backpack          # Works !

I have not tested writing to the CD-R/W drive yet, but I will post my successes or failures here.

- Enjoy
JMB365

---

### Post by haddog on 2005-10-29
[QUOTE=jmb365]Hi,

I have recently installed Breezy on a previously RH8 PC that was working fine with my MicroSolutions Parallel Port BackPack CD-R/W (Series 6).  After repeated attempts at trying to make it work on FC3, I gave up and decided to try Breezy.  This is my first experience of Ubuntu and I am impressed.  For those of you who want to connect this archaic external CD-R/W drive here is how to do it.  My script, which I stumbled upon after many RH8 tweaking days & nights are shown below.  It also works on Breezy!  All comment lines are included as possible fixes for your particular situation.  Make sure your BackPack is connected to the parallel port before booting and your BIOS setting for the parallel port is: PCSPP,TRISTATE,EPP

You can check the Parallel port setting by:
cat /proc/sys/dev/parport/parport0/modes

# Start here...

# modprobe parport		# Already maybe loaded
# modprobe parport_pc		# Already maybe loaded

modprobe paride

#
# The following 2 steps are not necessary on Breezy...
# 	mkdir /lib/modules/$(LINUX_VERSION)/misc
# 	cp /lib/modules/$(LINUX_VERSION)/kernel/drivers/block/paride/bpck6.o /lib/modules/2.4.20-20.8/misc/backpack.o

echo "Inserting the necessary modules..."
modprobe bpck6
modprobe pg		# For CD-R/W
modprobe cdrom
modprobe pcd		# For CD-R

dmesg | grep paride
# Look for: "paride: bpck6 registered as protocol 0"

# modprobe pcd drive0=0x378,1 drive1=0x3bc,1	# Example syntax
# To support such a wide range of devices PARIDE, the parallel port IDE subsystem, is actually structured in three parts.
# There is a base paride module which provides a registry and some common methods for accessing the parallel ports. 
# The second component is a set of high-level drivers for each of the different type of supported device:
# pd 	IDE disk
# pcd	ATAPI CD-ROM
# pf 	ATAPI disk
# pt 	ATAPI tape
# pg 	ATAPI generic devices

# The pg driver exists mainly to support parallel port ATAPI CD-R and CD-RW devices. 

#
# Run the commands below from a script 
# ====================================================================
echo "Running the commands of Check4CDDrives..."
test `whoami` = 'root' || echo "You must be root to execute the commands."
cdrecord -scanbus > /dev/null
if ! (pidof kerneld || test -f "/proc/sys/kernel/modprobe"); then
    echo "Neither kerneld nor kmod are running to automatically load modules".
fi
report_no_autoload() {
    echo "Ensure the module $1 is loaded automatically next time."
}
if test ! -f "/proc/scsi/scsi"; then
    report_no_autoload scsi_mod  &&  modprobe scsi_mod
fi
if ! grep "^........ sg_" /proc/ksyms > /dev/null; then
    report_no_autoload sg  &&  modprobe sg
fi
if ! grep "^........ sr_" /proc/ksyms > /dev/null; then
    report_no_autoload sr_mod  &&  modprobe sr_mod
fi
if ! grep "^........ loop_" /proc/ksyms > /dev/null; then
    report_no_autoload loop  &&  insmod loop
fi
if ! grep iso9660 /proc/filesystems > /dev/null; then
    report_no_autoload iso9660  &&  modprobe iso9660
fi
echo "The following is only needed for IDE/ATAPI CD-writers."
if ! grep ide-scsi /proc/ide/drivers > /dev/null; then
    report_no_autoload ide-scsi  &&  modprobe ide-scsi
fi
# ================================================================

# Now check if it is recognized:
cdrecord -scanbus

# Mount to an appropriate location after placing a CD in the drive
mkdir /mnt/backpack
mount -t iso9660 /dev/pcd0 /mnt/backpack
ls -al /mnt/backpack          # Works !

I have not tested writing to the CD-R/W drive yet, but I will post my successes or failures here.

- Enjoy
JMB365[/QUOTE]
Have you had any success using the USB connection? I have the Microsolutions Backpack 195200 model. It has both usb and paralell connections. Usb would write much faster.

---

### Post by jmb365 on 2005-11-07
Sorry I cannot test the USB method, since my BackPack does not have that option...

JMB

---

### Post by editrix on 2005-11-12
Hi jmb:

> I have not tested writing to the CD-R/W drive yet, but I will post my successes or failures here.

I have exactly the same setup, so I was hoping you would post.

Have you had any success? I have PCSPP & TRISTATE, but not EPP, and I'm reluctant to change my BIOS since the burner works perfectly in Windows. But, if I can get it working in Linux, I will.

---

