---
title: "How to Install SD Card Reader ENE Technology, Inc. (USB)"
date: 2011-06-06
forum: Hardware
---

### Post by Wilian on 2011-06-06
Howto get your netbook SD card reader working (this article is a litle modification from [http://community.linuxmint.com/tutorial/view/309](http://community.linuxmint.com/tutorial/view/309))
This  is a summary of the steps necessary to get my SD card reader working on  MSI Wind like netbook running. It involves downloading, building and  installing the driver module.
This is also relevant to other laptops/netbooks using the same internal card reader (ENE Technology UB6250). 
The source for this solution was [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530277](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530277). All credit goes to its contributors.
Disclaimer: Whilst I foresee no problems with this you copy the actions in this summary entirely at your own risk.

   1. Confirm that you have the relevant SD card reader that is not working and check kernel version.
   2. Install building tools.
   3. Download the driver module source.
   4. Extract the source files from the package.
   5. Build and install the module.
   6. Load the module and test.

1. Confirm that you have the same type of non-working SD card reader.

Insert an SD card into the card reader.

At a terminal type:

$ lsusb

you should see output like this:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 004: ID 0cf2:6250 ENE Technology, Inc.**
Bus 001 Device 002: ID 0402:9665 ALi Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

The 0cf2:6250 confirms you have the correct SD card reader for this howto.

Remove the SD card.

Check that your kernel: 

$ uname -r

2. Install building tools.

At a terminal:

$ sudo apt install build-essential

 
3. Download the driver module source.

Download this file:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530277/+attachment/1712997/+files/keucr.tgz](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530277/+attachment/1712997/+files/keucr.tgz)

back to top
4. Extract the package keucr.tgz

From a terminal cd to a working directory of your choice and extract the tar ball with:

$ cd <working directory path>

$ tar zxvf <path to downloaded file>/keucr.tgz

$ cd keucr

edit usb.c ($gedit usb.c) and change this:

If your kernel is < 2.6.34 search for
 "usb_alloc_coherent" and change to "usb_buffer_alloc"
and 
 "usb_free_coherent" and change to "usb_buffer_free"

Reason: [URL="http://lists-archives.org/linux-kernel/27314200-usb-rename-usb_buffer_alloc-and-usb_buffer_free.html"]http://lists-archives.org/linux-kernel/27314200-usb-rename-usb_buffer_alloc-and-usb_buffer_free.html
[/URL] 
Don`t forget to put the function prototypes after the last #include line according your kernel version:

for Kernel <2.6.34 put:
```

void usb_buffer_free (struct usb_device * dev,  size_t size,  void * addr,  dma_addr_t dma);

void * usb_buffer_alloc (struct usb_device * dev,  size_t size,  gfp_t mem_flags,  dma_addr_t * dma);
```
for Kernel >= 2.6.34 put:
```

void * usb_free_coherent (struct usb_device * dev,  size_t size,  gfp_t mem_flags,  dma_addr_t * dma);

void * usb_alloc_coherent (struct usb_device * dev,  size_t size,  gfp_t mem_flags,  dma_addr_t * dma);

```5. Build and install the module.

$ make -C /usr/src/linux-headers-`uname -r` M=`pwd`

$ sudo make -C /usr/src/linux-headers-`uname -r` O=/lib/modules/`uname -r`/build M=`pwd` modules_install

$ sudo depmod -a

update your initrd:

$ sudo update-initramfs -u -k `uname -r`

 
6. Try it out.

Insert your SD card.

See if it appears in Computer.

It should be mounted under /media.

At a terminal check that the module keucr is loaded with

$ lsmod

Check that the module keucr.ko is available with:

$ modprobe -l keucr

$ ls /lib/modules/`uname -r`/build/extra

Add keucr to /etc/modules listing:

$ sudo gedit /etc/modules

This file seens like that:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rt3090sta
**keucr**

```If no success please refer to the thread for more info and background. It worked for me. Good luck!

---

### Post by Knyquist on 2013-01-27
Hello!

I'm actually having problems with this bug, and with the solution proposed as well.

I'm running Xubuntu 12.04 (more than a fresh install) on an Emachines e350  (ENE's card reader).

I'm aware about the discussion on the Official Bug Report (and I'll post there also) but my problem is that I can't actually build the keucr module on my system.

With regards to the solution proposed in this thread, the compiling process stops because the compiler can't find a bunch of defines, more specifically:

#define US_PR_BULK  0x50
#define US_SC_SCSI  0x06
#define US_PR_CBI   0x00
#define US_SC_CYP_ATACB 0xf1
#define US_PR_CB        0x01
#define US_SC_UFI       0x04
#define US_PR_DPCM_USB  0xf0
#define US_SC_RBC       0x01

which in previous versions of the kernel were defined in usb_usual.h .
By adding these defines to usb.h file in the keucr directory, you are actually able to compile the module without mistakes.

But of course, I guess this is not a proper solution to apply. In fact, at the end, it still doesn't work.

Thus, I am still searching for a proper solution of the problem.

What I can say is that before upgrading to Xubuntu 12.04 I was running Ubuntu Maverick 10.10 . At that time I had the Card Reader working by simply upgrading the kernel to 2.38.XX (I can't remember the XX part^^) - while keeping Maverick.
So this could be a good hint for further investigation on this bug.

I hope this problem will be solved in a short time but I guess this won't be the case, unless a lot of people start to face the same issue by upgrading their systems.

If you are aware about other solutions, or if I'm missing some part, please let me know.
Thanks and best regards.

In any case I'll keep an eye on this thread!

---

### Post by howefield on 2013-01-27
Old thread closed.

---

