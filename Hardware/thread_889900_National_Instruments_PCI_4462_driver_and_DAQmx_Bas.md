---
title: "National Instruments PCI 4462 driver and DAQmx Base Install"
date: 2008-08-14
forum: Hardware
---

### Post by philwinder on 2008-08-14
Edit:
I have just found out that the DAQmx Base version does not support the pci-4462.  So I have attempted to install the original daqmx suite.  Unfortunately I cant.  It complains about not finding the correct kernal headers for this version of the kernal.

******************************** ERROR ****************************************
* Kernel source in /lib/modules/2.6.24-20-generic/build does not appear to be
* configured for the 2.6.24-20-generic kernel.
* Configuration of kernel source is required to continue installation.        *
* Refer to the README file for the product you are installing for information *
* about configuring your kernel source.                                       *
******************************** ERROR ****************************************

Hope that formatting stays ok.

Cheers


Hi,
I was just wondering whether anyone had any luck installing and using NI's DAQmx Base driver software?  
I have managed to install it via alien from the redhat rpm's, but I cant get the hardware to work.  Every time I use lsdaq, it cannot find any devices.  Also lspci returns "00:0b.0 Class ff00: National Instruments Unknown device 7170".

So generally, I think I have the software installed ok, (not sure how to check though!) but I cant find a way to tell the hardware that there is a driver for it.  Is there some way of forcing this in ubuntu?

Thanks,
Phil Winder

---

### Post by geoffjay on 2009-08-12
I know that this post is over a year old but I was wondering if you ever had any luck getting an NI PCI card to work with DAQmx base? I've been able to get a couple of the USB devices to work under OpenSUSE but I've never had any luck using Ubuntu + alien.

---

### Post by philwinder on 2009-08-13
I gave up after finding my card was not currently supported and I stuck with xp. I think the ubuntu + alien did work, but it didn't find my card because it wasnt supported. Check that yours is, and it should be ok.

Phil

---

