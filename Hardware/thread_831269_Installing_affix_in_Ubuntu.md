---
title: "Installing affix in Ubuntu"
date: 2008-06-16
forum: Hardware
---

### Post by ztrange on 2008-06-16
Hi I'm trying to install the affix module 

[http://affix.sourceforge.net/index.shtml#news](http://affix.sourceforge.net/index.shtml#news)

Its a bluetooth protocol stack and I think I'd work in replace of bluez. My hardware says to be supported by it in the supported hardware list.

However, when I read the install instructions fro Debian in 

[http://affix.sourceforge.net/affix-end-user/1.1/c39.html](http://affix.sourceforge.net/affix-end-user/1.1/c39.html)

the first thing it says is that I have to configure my kernel with make menuconfig and I know those are kin of compilign commands, however, I dont know where should I launch those commands nor if I have the kernel source to compile it and how dangerous it is.

Well, any help will be appreciated.

Sorry for my ugly english

---

### Post by ztrange on 2008-06-21
Ok, I've found some info in the internet and now I'm trying to disable the modules needed to be disabled for affix:

In the Affix installation manual says
> You have to configure you kernel before you can start installing Affix kernel module. To configure your kernel directory and use command make menuconfig to configure your kernel. Then,

    * disable "Bluetooth support" (Bluez) support on Networking support page
    * disable "USB Bluetooth TTY support" on USB support page
    * enable support for USB devices
    * enable support for PCMCIA device
    * enable yenta_socket support
    * enable support hot plug devices
    * enable DEVFS device file system. This is highly recommended.
    * enable support for PPP


But now I don't know what modules should I affect, there is a Networking and others but I don't see the USB support. I'm affraid of messing something up but I'll keep trying. Any help will be appreciated.

This is the list of Options in my make menuconfig:

General setup  --->
[*] Enable loadable module support  --->
[*] Enable the block layer  ---> 
Processor type and features  ---> 
Power management options  --->
Bus options (PCI etc.)  --->
Executable file formats / Emulations  ---> 
Networking  --->
Device Drivers  --->
Firmware Drivers  --->
File systems  --->
*] Instrumentation Support  --->
Kernel hacking  --->
Security options  --->
-*- Cryptographic API  --->
[*] Virtualization  --->
Library routines  --->

---

