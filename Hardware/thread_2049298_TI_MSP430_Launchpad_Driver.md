---
title: "TI MSP430 Launchpad Driver"
date: 2012-08-28
forum: Hardware
---

### Post by vksalian on 2012-08-28
Hi,

We are trying to test MSP 430 Launchpad kits of Texas Instruments under Ubuntu. But we could not find USB driver for the same. We tried to install the drivers from source codes available in net, but the drivers are supported for kernel versions 2.4 and 2.6 only, while present Kernel versions are 3.0 in 12.04 LTS. Is there any way so that we can fix this. 

Please help us in this regard.

Thanks,
VKSALIAN.

---

### Post by SuppoTaalasmaa on 2012-09-17
> **vksalian said:**
> Hi,

We are trying to test MSP 430 Launchpad kits of Texas Instruments under Ubuntu. But we could not find USB driver for the same. We tried to install the drivers from source codes available in net, but the drivers are supported for kernel versions 2.4 and 2.6 only, while present Kernel versions are 3.0 in 12.04 LTS. Is there any way so that we can fix this. 

Please help us in this regard.

Thanks,
VKSALIAN.

Hi VKSALIAN,

I didn't see any problems just installing the packages provided by Canonical in the package manager.
I am running 64bit 12.10, and following packages got me up and running:
binutils-msp430 gcc-msp430 gdb-msp430 msp430-libc msp430mcu mspdebug srecord libsrecord-dev libgmp-dev

There was a problem with gdb-msp430_7.2~mspgcc-7.2-20110612-1ubuntu4_amd64.deb 
But aptitude solved that automagically by just issuing apt-get -f install

After that I was able to compile example program and run the debugger with: sudo mspdebug rf2500

from dmesg my device was connected as ttyACM0

Hope this helps!

---

