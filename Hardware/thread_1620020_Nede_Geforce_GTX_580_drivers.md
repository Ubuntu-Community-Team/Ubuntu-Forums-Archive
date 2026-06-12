---
title: "Nede Geforce GTX 580 drivers"
date: 2010-11-12
forum: Hardware
---

### Post by Sanhime on 2010-11-12
Hello.  Using 10.04 and I need drivers for Geforce GTX 580.  The Hardware Driver search could not find drivers.  Any solutions?  Thanks.

---

### Post by xenogia on 2010-12-01
Hi Sanhime,

I don't think the linux binaries of the Nvidia drivers actually support the 580 card as of yet.  Your probably going to have to wait till the next update.

---

### Post by cascade9 on 2010-12-02
The nvidia-current drivers in 10.04 wont support the GTX80- you will need to d/l and instll the nvidia drivers manually. 

[http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us)

Directions for how to install- 

[http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)

Change "NVIDIA-Linux-x86_64-195.36.24-pkg2.run" to suit the drivers you are installing (should be 260.19.11)

---

### Post by xannen on 2011-04-29
Hi

I'm new to Linux and Ubuntu.  I've just recently installed Ubuntu  11.04.  Next,I installed the recommended Nvidia driver via: System >  Administration > Additional Drivers > Nvidia accelerated graphics  drivers [recommended].

Here are the Nvidia X Server Settings:

X Server Information

Operating System: Linux-x86_64
NVIDIA Driver Version: 270.41.06

X Server Information

Display Name: server1:0
Server Version Number: 11.0
Server Vendor STring: The X.Org Foundation
Server Vendor Version: 1.10.1 (11001000)
NV-CONTROL Version: 1.26
Screens: 1

GPU 0 - (GeForce GTX 580)

Graphics CArd Information

Graphics Processor: GeForce GTX 580
CUDA Cores: 512
VBIOS Version: 70.10.17.00.00
Memory: 1536
Memory Interface: 384-bit

Bus Type: PCI Express x16 Gen2
Bus ID: PCI:1:0:0
PCI Device ID: 0x1080
PCI Vendor ID: 0x10de
IRQ: 16

PCI-E Max Link Speed: 5000

X Screens: Screen 0


Will this driver installation allow me to make use of all the drivers features and specification?

---

