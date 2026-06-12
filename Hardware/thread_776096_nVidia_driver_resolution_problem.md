---
title: "nVidia driver resolution problem"
date: 2008-04-30
forum: Hardware
---

### Post by M_C_E on 2008-04-30
I just installed Ubuntu. Installed the nVidia drivers for Linux for my card (GeForce 5500). The resolution dropped from 1024x768 to 680x480 and I am unable to change back to the previous resolution.

Any ideas on how to fix this problem will be greatly appreciated. :confused:

thanks!

MCE

p.s.  this is my first time using linux.

---

### Post by ajv2003 on 2008-04-30
My unit has that same GPU and Hardy Heron auto installed no problem. I thought in Linux drivers were not needed. In addition I just installed on a 6 month old HP notebook and the nVidia driver and all the hardware and services installed from the CD. Nothing was required. Welcome to Linux this is not Windows.

---

### Post by DandyDon on 2008-05-01
> **M_C_E said:**
> I just installed Ubuntu. Installed the nVidia drivers for Linux for my card (GeForce 5500). The resolution dropped from 1024x768 to 680x480 and I am unable to change back to the previous resolution.

Any ideas on how to fix this problem will be greatly appreciated. :confused:

thanks!

MCE

p.s.  this is my first time using linux.

Google EnvyNG, follow his instructions to remove the drivers you have using the Terminal, located under Applications-Accessories. I just Copy / Paste-d his scripts into Terminal.

Then follow his instructions on downloading and installing EnvyNG. It will install under Applications-System Tools. Run the Program. It will download the latest Nvidia Linux driver from the Nvidia site, install it, and configure your display. 

The new driver GUI can be found under System-Administration-NvidiaXServer Settings. You can change / check settings there.

I had the same trouble you have, EnvyNG seems to be a better utility than the one packaged with Ubuntu. 

How many times has that been true with Windows,eh?.

---

