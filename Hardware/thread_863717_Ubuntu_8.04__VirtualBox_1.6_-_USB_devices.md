---
title: "Ubuntu 8.04 / VirtualBox 1.6 - USB devices"
date: 2008-07-18
forum: Hardware
---

### Post by Kernel Kev on 2008-07-18
After having a good look all over the net and finding different variations of similar problems i am having, i failed to find someone with the same problem i am having... maybe this is because im missing something so simple!

Ok basically i have Ubuntu 8.04 LTS and i am running VirtualBox with Windows XP and Vista as guest OS's.  These both boot and run perfectly fine (faster than if they was Host os's if i may say so).

Now, somehow i managed to add my USB devices to the OS's in virtualBox's settings and they all come up with the auto inserted filter settings.

I insert my USB pen and i have USB enabled etc and i unmount the device from Ubuntu and load the host OS (XP).  Here is where it goes wrong, XP dosent recognise my flash drive and i go to Devices>USB Devices in the VB console but the devices are listed but not "clickable"...

Whats wrong, i dont understand what i done wrong...

Any help would be great.

---

### Post by lswb on 2008-07-18
I may be corrected by someone more knowledgeable, but I believe the version of virtualbox in the repositories does not support usb. See 

[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

---

### Post by L815 on 2008-07-19
Try downloading the version from Sun's website. 

There is a Open Source version, and a regular version. 
Get the regular version.

Direct Link:
[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

---

### Post by Kernel Kev on 2008-07-19
Hi i believe i have the regular version as i got the program from this link:
[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

The page before this says about Open Source Edition below it which is a separate download.

About the USB repository not being supported, i heard this too however i managed to add the usb devices into the Virtual box but cannot activate them from inside windows... Is this what they mean by not supported yet?

If this is the case i hear that installing 1.5.2 (the gusty version) works, but i am going to need to uninstall VirtualBox 1.6 first and remove all the OS's... any good suggestions on doing this?

Thanks

---

