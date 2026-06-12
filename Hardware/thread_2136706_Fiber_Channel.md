---
title: "Fiber Channel"
date: 2013-04-18
forum: Hardware
---

### Post by darinschmidt on 2013-04-18
Is this the best method to share zvol block devices over fiber or is there a better method than what i had been using on openfiler?

I am switching from openfiler to ubuntu server 12.04. With openfiler i used scst to share drives over my fiber channel using iscsi. I have qla2300 fiber cards. I downloaded the scst trunk.

```
svn co https://scst.svn.sourceforge.net/svnroot/scst/trunk scst
```

scst was downloaded into /tmp and i did a make all and make install (this is the first time i have used make so i am assuming that it installed all the componenets in the scst directory to my server).

I followed the instructions from here: [http://www.servethehome.com/set-infiniband-srp-target-ubuntu-1204/](http://www.servethehome.com/set-infiniband-srp-target-ubuntu-1204/)
And the link above provided instructions as well. Everything seems to be fine aside from the qla drivers not being laoded (i havent restarted the server yet to see if that helpd) but my question is, is this the best way to share zvol (block device) over iscsi through fiber to my other servers using Ubuntu Server 12.04 64bit.

There is no qla2x00tgt in /etc/init.d so i dont know how to start/restart the service and the script i have from openfiler wont work because the syntax is different and i have no idea how to correct it as i havent used Ubuntu/debian enough to know the difference in syntax. The reason i know the driver isnt active is because i issue scstadmin -enable_target <WWN> and it tells me that the driver '' isnt available or loaded.

The qla2x000tgt script for openfiler can be found here: [https://forums.openfiler.com/index.php?/topic/5814-qla2x00tgt-not-found/](https://forums.openfiler.com/index.php?/topic/5814-qla2x00tgt-not-found/) 5 posts down is the openfiler qla2x000tgt init.d script

---

### Post by lucky00000007 on 2013-04-19
Hi,

I am taking a similar approach and am stuck while starting qla2x00tgt services.

system says unrecognized service.

please help.

regards

---

### Post by darinschmidt on 2013-04-23
yes, that is because there is no qla2x00tgt in /etc/init.d. i cant figure that part either. i "make all" and "make install" in the scst trunk directory but yet doesnt seem that everything appears to be installed. I downloaded the firmware from qlogics site and threw them in the directory that i cant recall off hand (bin files) because only qla2xxx was there which seems to be the only one loading.... I noticed too that in the dmesg log that its detecting the QLA2322 as an ISP2322.... Im not a linux guru, so im trying to piece this all together. But i did notice that when i tried to compile the qla drivers manually from the scst trunk that it failed stating that some qlaxxx.h:x:x file or directory was missing. The file is there but may not be able to read something within the file. I may switch back to Openfiler or try CentOS if i cant get this working in the next week.... Had no issues with Openfiler 2.99.

Such a shame because i like Ubuntu too.

---

### Post by darinschmidt on 2013-04-23
I think the only part i have issues with though now is that scstadmin -list_drivers shows no drivers. Not sure how to get it to see and use the qla2xxx driver that is used currently to load the fiber cards as seen in dmesg log

---

### Post by JoeDM09 on 2013-06-18
I don't think setting up SCST for fibre channel is as easy as installing the application. I'm new to this myself and not having too much luck but I understand that you need to patch the drivers into your kernel, build it and boot into the new kernel. I always hit issues when building a 3.X kernel so I am trying it as we speak on Ubuntu 10.04 with the 2.6.32 kernel. I'll come back with instructions if it works.

---

### Post by JoeDM09 on 2013-06-19
Got it working using these two guides merged:[http://scst.sourceforge.net/qla2x00t-howto.html](http://scst.sourceforge.net/qla2x00t-howto.html) and [http://www.tomlecluse.be/blog/20110902/scst-and-scstadmin-ubuntu-1104](http://www.tomlecluse.be/blog/20110902/scst-and-scstadmin-ubuntu-1104) I've done up a guide below. Its a bit basic but should be easy to follow if you use common sense to edit it to match your kernel, etc.

---

### Post by JoeDM09 on 2013-06-19
Install SCST with QLogic Drivers

# First Make sure you are able to see the boot menu and change boot options.
nano /etc/default/grub
"# out hidden boot and timeout and save"
update-grub

# Install pre-requisites for build
apt-get install fakeroot kernel-wedge build-essential makedumpfile kernel-package libncurses5 libncurses5-dev gcc libncurses5-dev linux-headers-$(uname -r) lsscsi patch subversion
apt-get build-dep --no-install-recommends linux-image-$(uname -r)

# Make sure QLogic firmware is available
ls /lib/firmware/ | grep ql*

# If missing then download firmware from [http://ldriver.qlogic.com/firmware/](http://ldriver.qlogic.com/firmware/)
# (for debian to install firmware)
mkdir /root/tmp
cd /root/tmp
wget [http://ftp.au.debian.org/debian/pool/non-free/f/firmware-nonfree/firmware-qlogic_0.28+squeeze1_all.deb](http://ftp.au.debian.org/debian/pool/non-free/f/firmware-nonfree/firmware-qlogic_0.28+squeeze1_all.deb)
dpkg -i firmware-qlogic_0.28+squeeze1_all.deb
ls /lib/firmware/ | grep ql*

# Download SCST Trunk including the QLogic Target Drivers
cd /root
svn co [https://scst.svn.sourceforge.net/svnroot/scst/trunk](https://scst.svn.sourceforge.net/svnroot/scst/trunk) scst

# Unload the system default drivers
rmmod qla2xxx
echo blacklist qla2xxx >/etc/modprobe.d/blacklist-qla2xxx.conf

# Download and install your kernel source and link the /usr/src/linux
cd /usr/src
apt-get install linux-source-2.6
tar xjf linux-source-2.6.32.tar.bz2
ln -s /usr/src/linux-source-2.6.32 Linux

# Patch source kernel to prepare to load SCST QLogic drivers (I'm sure theres more to it)
cd /usr/src/linux-source-2.6.32
patch -p1 < /root/scst/scst/kernel/scst_exec_req_fifo-2.6.32.patch

# Copy running config file to be used in new kernel
cp -vi /boot/config-`uname -r` .config

# Backup kernel original QLogic drivers and link to SCST QLogic drivers.
mv /usr/src/linux/drivers/scsi/qla2xxx /usr/src/linux/drivers/scsi/qla2xxx_orig
ln -s ~/scst/trunk/qla2x00t /usr/src/linux/drivers/scsi/qla2xxx

# Make menuconfig and ensure QLogic target mode is selected following the below route. 
make menuconfig
Device Drivers->SCSI device support->SCSI low level drivers->Qlogic 2xxx target mode support

# make the build faster if you have multiple cores
export CONCURRENCY_LEVEL="number of CPU cores plus 1"

# Build the kernel into a deb package
cd /usr/src/linux
make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-scst kernel-image kernel-headers

# Install new kernel
cd /usr/src/
dpkg -i linux-image-2.6.32-scst_2.6.32-scst-10.00.Custom_amd64.deb
dpkg -i linux-headers-2.6.32-scst_2.6.32-scst-10.00.Custom_amd64.deb

### In Ubuntu you may need to update the RAM disk before reboot. Google the process but I think it is:
update-initramfs -u

reboot

# boot into newly installed kernel

# Select a build mode that suits your needs, e.g. optimal performance or debugging SCST. The default mode is debug mode. Here is how to switch to release mode:
cd /root/scst
make 2release

#Now build the SCST kernel modules.
cd /root/scst/scst/src
make all
make install

# Build the QLogic target driver as follows:
cd /root/scst
BUILD_2X_MODULE=y CONFIG_SCSI_QLA_FC=y CONFIG_SCSI_QLA2XXX_TARGET=y \
make -s -C qla2x00t/qla2x00-target install
ls -l /lib/modules/`uname -r`/extra/qla2*

#Insert the kernel modules with the 'modprobe' program and add to startup modules
nano /etc/modules
# Add the below text to the bottom and save /etc/modules
"
scst
qla2xxx_scst
qla2x00tgt
scst_vdisk
scst_user
scst_disk
"

# Manually load the modules or reboot.
modprobe scst
 modprobe qla2xxx_scst
modprobe qla2x00tgt
modprobe scst_vdisk
modprobe scst_user
modprobe scst_disk


# Locate and record Target WWN(s)
cat /sys/class/fc_host/host*/port_name

# Install SCST Admin
cd /root/scst/scstadmin
make
make install
 
# Configure QLogic Device, Create Group, Create Virtual Disk, Create LUN and group it all together.
scstadmin -enable_target "target WWN" -driver qla2x00t
scstadmin -add_group "group name" -driver qla2x00t -target "target WWN"
scstadmin -add_init "initiator wwn" -driver qla2x00t -target "target wwn" -group "group name"
scstadmin -add_init "additional initiator wwn" -driver qla2x00t -target "target wwn" -group "group name"

# "Create and use virtual Drive as LUN"
# "will take ages, using disk1 located at /mnt/ as example file path"

dd if=/dev/zero of="file path" bs="size in kb" count=512
ls -l /mnt/disk1
file /mnt/disk1

scstadmin -open_dev "VD Name being disk1" -handler vdisk_fileio -attributes filename=/mnt/disk1
scstadmin -add_lun "lun ID" -driver qla2x00t -target "Target WWN" -group "group name" -device "VD Name being disk1"
scstadmin -write_config /etc/scst.conf


###Still working on issue where script /etc/init.d/scst does not run on boot.

---

### Post by JoeDM09 on 2013-06-25
I finally got it all working perfectly. Since the /etc/init.d/scst script has issues starting up I just ended up adding the line:
"
sudo scstadmin -config /etc/scst.conf
"
to the /etc/rc.local file
All feedback is welcome.

---

### Post by Nick_Murphy on 2013-09-02
I just went through these steps yesterday and it works like a charm. Thanks for putting this up

---

### Post by thaynes2 on 2014-01-04
what version of ubuntu were you running for this guide?

I am on 12.04

I get this error 

apt-get install linux-source-2.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-source-2.6 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'linux-source-2.6' has no installation candidate

---

### Post by Nick_Murphy on 2014-01-08
I'm using 12.10 and used linux-source-3.2.0 from memory. I have done this twice on 2 different machines and they both worked perfectly.

---

### Post by alejbaca on 2014-01-09
I am currently trying to load the module qla2xxx_scst however I am encountering an error:

```
FATAL: Error inserting qla2xxx_scst (/lib/modules/3.2.53-scst/extra/qla2xxx_scst.ko): Device or resource busy
```

I added the module into modprobe program in /etc/modules and rebooted the server but I am still not seeing qla2xxx_scst or qla2x00tgt when I perform the command lsmod.
I checked  dmesg and it is spitting out this message:

```
Error: Driver 'qla2xxx' is already registered, aborting...
```

Any suggestions?

---

### Post by Johan_Christensson on 2014-03-20
Hi everyone.

I have followed the guide above but I get stuck at the part when buildning SCST modules.

If i execute the command "sudo make all" in the SCST source directory, I get the following error:

  CC [M]  /usr/src/scst/scst/src/dev_handlers/scst_vdisk.o
/usr/src/scst/scst/src/dev_handlers/scst_vdisk.c:1430:2: error: ‘COMPARE_AND_WRITE’ undeclared here (not in a function)
/usr/src/scst/scst/src/dev_handlers/scst_vdisk.c:1430:2: error: array index in initializer not of integer type
/usr/src/scst/scst/src/dev_handlers/scst_vdisk.c:1430:2: error: (near initialization for ‘blockio_ops’)
/usr/src/scst/scst/src/dev_handlers/scst_vdisk.c:1448:2: error: array index in initializer not of integer type
/usr/src/scst/scst/src/dev_handlers/scst_vdisk.c:1448:2: error: (near initialization for ‘fileio_ops’)
/usr/src/scst/scst/src/dev_handlers/scst_vdisk.c:1463:2: error: array index in initializer not of integer type
/usr/src/scst/scst/src/dev_handlers/scst_vdisk.c:1463:2: error: (near initialization for ‘nullio_ops’)
make[5]: *** [/usr/src/scst/scst/src/dev_handlers/scst_vdisk.o] Error 1
make[4]: *** [/usr/src/scst/scst/src/dev_handlers] Error 2
make[3]: *** [_module_/usr/src/scst/scst/src] Error 2
make[3]: Leaving directory `/usr/src/linux-lts-saucy-3.11.0'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/src/scst/scst/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/scst/scst'
make: *** [all] Error 2

I have gone though all the steps to make sure that I haven't missed any thing, and I even did everythin all over again, but I still ended up at the same point.

Any ideas?

/Johan Ch

---

### Post by Johan_Christensson on 2014-03-21
Actualy, my problem got solved when I re-downloaded the SCST source files. I noticed on the mailinglist the mention of this function, so I guess that i got hold of a "interim build" or something like that. When I downloaded a new copy a few hours later, everything worked as expected.

/Johan Ch

---

