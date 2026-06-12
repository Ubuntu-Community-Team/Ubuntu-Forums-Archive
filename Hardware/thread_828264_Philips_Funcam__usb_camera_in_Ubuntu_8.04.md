---
title: "Philips Funcam  usb camera in Ubuntu 8.04"
date: 2008-06-13
forum: Hardware
---

### Post by dnaga57 on 2008-06-13
I have Philips Funcam web cam attached in usb . On lsusb I get the following
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 004: ID 05b8:3038 Agiler, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 0471:0321 Philips FunCam
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 018: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 001 Device 017: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 016: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 001 Device 015: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 001 Device 014: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 001 Device 001: ID 0000:0000  
but the system does not seem to detect it. Any hhelp please:confused:

---

### Post by dnaga57 on 2008-08-13
I have downloaded pwc drivers - still it is not working
Help please

---

### Post by dnaga57 on 2008-08-13
Some more info
    

Re: Philips Funcam Webcam drivers & installation

Postby dnmint on Sun Aug 10, 2008 6:02 am
Can I bump this for help
My results for lsusb - Philips is the webcam with built in mike.
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 002: ID 05b8:3038 Agiler, Inc.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 0471:0321 Philips
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 008: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 001 Device 007: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 006: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 001 Device 005: ID 0b97:7761 O2 Micro, Inc.
Bus 001 Device 004: ID 413c:a005 Dell Computer Corp.
Bus 001 Device 001: ID 0000:0000

The instructions are
Kernel 2.6 + module
- - - - - - - - -

1) download the file [http://www.saillard.org/linux/pwc/files](http://www.saillard.org/linux/pwc/files) ... c1.tar.bz2
(or the last available file on the site)
2) unpack the file using the command command:
# tar xjf pwc-10.0.9-rc1.tar.bz2
3) compile the module (this needs the source of your actual kernel to
be installed)
# cd pwc-10.0.9rc1
# make
4) login as root
# su
5) In case an older version of the module was already installed, use
the following commands to delete that module, if not go to 6)
# find /lib/modules/`uname -r`/ -name "pwc*.ko*"
# rm <name of the file.ko>
6) Copy the new modules to the old ones
# make install
or
# cp pwc.ko <path to the folder of original pwc.ko module>
For example: /lib/modules/`uname -r`/{misc,extra}
# depmod -a
7) Unload the old module(s) or reboot the machine
# rmmod pwc
# rmmod pwcx
# modprobe pwc

Kernel 2.6 + patch
- - - - - - - - -

1) download the patch [http://www.saillard.org/linux/pwc/patches/](http://www.saillard.org/linux/pwc/patches/) that
matches your kernel
viz.: linux-2.6.13_pwc-10.0.8.patch.bz2 for a 2.6.13 kernel
2) download the linux source from [http://www.us.kernel.org/](http://www.us.kernel.org/)
3) unpack the source of the Linux kernel
# tar xjf linux-2.6.13.tar.bz2
# cd linux-2.6.13
4) patch the kernel
# bzcat ../linux-2.6.13_pwc-10.0.8.patch.bz2 | patch -p1
5) compile the kernel as usual
# make menuconfig
# make
# make install modules_install

Translated by Rob Teng

Attachments

    linux-v4l_pwc.10.0.12-1.patch.bz2
        The driver file zipped These are later versions than 10.0.9 refrred in instructions.
        (48.43 KB) Not downloaded yet

    pwc-10.0.12-rc1.tar.bz2
        The patch file zipped
        (47.72 KB) Not downloaded yet

---

### Post by dnaga57 on 2008-08-13
Re: Philips Funcam Webcam drivers & installation

Postby dnmint on Sun Aug 10, 2008 7:26 am
I am adding one more link
[http://www.lavrsen.dk/twiki/bin/view/PWC/WebHome](http://www.lavrsen.dk/twiki/bin/view/PWC/WebHome)
This gives instructions for installation- not clear to me.
I will need 'dummy type' help
Thank

---

