---
title: "Need help installing drivers for MEMSense Nano IMU"
date: 2008-02-22
forum: Hardware &amp; Laptops
---

### Post by robotool on 2008-02-22
Hey all,

I'm working on a robotics project for college and I'd like to use a MEMSense Nano IMU.  The company has a pretty complete set of example code, but all of it was written for Windows.  I'm trying to port the sections of their code that actually communicate with the device for use in Ubuntu; this basically reduces to replacing a certain set of calls to a Windows version of a Silicon Labs library with calls to the corresponding Linux version.  Silicon labs has the software available for download here: [http://www.silabs.com/public/documents/software_doc/drivers/Microcontrollers/USB/en/linux_VCP_v26_driver_src.zip](http://www.silabs.com/public/documents/software_doc/drivers/Microcontrollers/USB/en/linux_VCP_v26_driver_src.zip)

The contents of this .zip file include a .rpm.  I've installed .rpm's before using alien, but this one doesn't seem to be installing properly.  I think that part of the problem is that it's looking for the ubuntu kernel source as part of its installation, and I'm not sure where that's located or how to tell the configuration script where to find it.

Any help with this would be greatly appreciated :-).

---

