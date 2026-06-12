---
title: "HighPoint RocketRaid 620 - Marvell 88SE9128 Chipset"
date: 2011-04-10
forum: Hardware
---

### Post by Fentanyl on 2011-04-10
I would like to buy that RAID sata 3 controller to make a RAID1 (i need windows too, so.. no, i cannot use mdadm).
This is the card: [http://www.highpoint-tech.cn/USA/rr620.htm](http://www.highpoint-tech.cn/USA/rr620.htm)

Don't tell me "ohh look at the drivers page" because no one successfully compiled the linux generic drivers.
Now.. the card is based on MARVELL 88SE9128 chipset and from this page:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/658521](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/658521)

I see that this chipset is now supported from Kernel but.. integrated on mainboard and pci-express... are same things?

Any experience about this card?

---

### Post by Fentanyl on 2011-04-10
I've read this

[https://help.ubuntu.com/community/RocketRaid](https://help.ubuntu.com/community/RocketRaid)

But if i try to compile the driver on ubuntu 11.04:

daniele@daniele-ubuntu:~/raid/product/rr62x/linux$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/daniele/raid/product/rr62x/linux/.build/os_linux.o
In file included from /home/daniele/raid/product/rr62x/linux/.build/os_linux.c:6:0:
/home/daniele/raid/osm/linux/osm_linux.h:12:26: fatal error: linux/config.h: No such file or directory
compilation terminated.
make[2]: *** [/home/daniele/raid/product/rr62x/linux/.build/os_linux.o] Error 1
make[1]: *** [_module_/home/daniele/raid/product/rr62x/linux/.build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [rr62x.ko] Error 2

So i guess the only availabe driver is too old for this kernel, config.h si for and old one....
in other words, if i'll buy that card i suppose it won't work....

---

### Post by R.MnTnA on 2011-05-16
I used the method described by the post on the bottom of this page and it worked-
[https://help.ubuntu.com/community/RocketRaid](https://help.ubuntu.com/community/RocketRaid)
Originally Posted on this forum by                                   niels.horn
                              
- 
[http://www.linuxquestions.org/questions/slackware-14/highppint-rocketraid-2320-driver-breaks-current-2-6-37-4-a-869636/](http://www.linuxquestions.org/questions/slackware-14/highppint-rocketraid-2320-driver-breaks-current-2-6-37-4-a-869636/)

> Removed the linux/config.h include statement from os_linux.h
 Modified the method call to blkdev_get at approximately line 348 of os_linux.c
```
blkdev_get(bdev, FMODE_READ, NULL) 
```> The additional parameter is NULL>  Appended the following to osm_linux.c> Replace this line  static int hpt_queuecommand (Scsi_Cmnd * SCpnt, void (*done) (Scsi_Cmnd *))  with this  ```
static int hpt_queuecommand_lck (Scsi_Cmnd * SCpnt, void (*done) (Scsi_Cmnd *)) 
```> Before the hpt_reset method, 
I appended the following lines ```
#ifdef DEF_SCSI_QCMD DEF_SCSI_QCMD(hpt_queuecommand) 
#else 
define hpt_queuecommand hpt_queuecommand_lck 
#endif[

```In other words put that above the line that states 
static int hpt_reset (Scsi_Cmnd *SCpnt)


Big Thanks to niels.horn for that! You Rock! :guitar:

I then built it into a new kernel using the readme directions from the drivers package.

```
#############################################################################
3. Using the driver as a kernel patch
#############################################################################

     You must have a full kernel source tree to use the driver as a patch.
     To patch a kernel source tree, run the command
     
        # cd rr62x-linux-src-v1.xx/product/rr62x/linux/
        # make patchkernel KERNELDIR=<kernel-source-dir>
        
     For an unconfigured 2.6 kernel source tree, include/linux/version.h may
     not exist so you should add "KERNEL_VER=2.6" to the command:

        # make patchkernel KERNELDIR=<kernel-source-dir> KERNEL_VER=2.6
        
     Then you can configure the driver into kernel during the kernel 
     configuration process (e.g. "make menuconfig"). It is listed under
     scsi low level drivers.
     
     Below is an example to make and install a kernel with the driver built-in:
     
        # cd /usr/src/linux-2.6.30
        # make menuconfig
        
        Select "Device Drivers --->" and press enter.
        Select "SCSI device support", then press 'Y' to make it built-in.
        Select "SCSI disk support" then press 'Y' to make it build-in.
        Select "SCSI low-level drivers --->" and press enter.
        Select "HighPoint RocketRAID 62x support" and press 'Y'.
        Exit and save the kernel configuration.
        
        # make
        # make modules_install
        # make install
        
        Then you can reboot from the new kernel.
```

---

