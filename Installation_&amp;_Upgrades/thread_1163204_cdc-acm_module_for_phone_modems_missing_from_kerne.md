---
title: "cdc-acm module for phone modems missing from kernel 2.6.28-11-generic"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by skippuff54 on 2009-05-18
The cdc_acm.o module for data interfaces, i.e. phone modems, is missing from kernel 2.6.28-11-generic and therefore all variants that use this kernel.

I discovered the missing module while trying to connect my Motorola phones as modems. See description here: [http://ubuntuforums.org/showthread.php?t=1162437]("http://ubuntuforums.org/showthread.php?t=1162437")

In this thread, I explain my workaround is to compile kernel 2.6.29.3 from source (plus manually add an entry for the Motorola QA30 phone).

Launchpad [https://bugs.launchpad.net/ubuntu/+bug/377739]("https://bugs.launchpad.net/ubuntu/+bug/377739")

---

### Post by skippuff54 on 2010-05-21
**[SIZE="3"]Update:[/SIZE]** The cdc_acm module and associated files are included in the latest version of Ubuntu - 10.04 Lucid Lynx with kernel 2.6.32-22-generic.

The phone issue that I detailed in the referenced post may have something to do with the usbserial module being moved into/out of the kernel recently.

---

### Post by wjpowers on 2010-12-08
I am using Ubuntu Lucid and I still have problems with being able to establish a connection with my cell phone (motorola w755).

Lucid does have cdc-acm, but I have to do a modprobe to load the module.  
But even after loading module Iwhich I can detect with an lsmod), when I connect my phone through a usb port, it is not connected to ttyacm0. 

The phone is detected as tailing dmesg shows, but cdc-acm never gets involved and it is not associated with ttyacm0.

Even if I 
sudo mknod /dev/ttyACM0 c 166 0
and the char device ttyACM0 is created, when I connect the phone, it is still not connected to ttyACM0.

I am trying to use (perhaps foolishly) moto4lin.  Moto4lin detects the cell phone as an AT device. But i don't know what to do with that.  I'm trying to be able to download pictures.

Any help would be appreciated.

thanks,

bill powers

---

