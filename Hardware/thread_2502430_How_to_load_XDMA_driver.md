---
title: "How to load XDMA driver?"
date: 2024-11-14
forum: Hardware
---

### Post by hobbss on 2024-11-14
Earlier, this year, Xilinx (AMD) got their XDMA driver approved for integration in to the kernel (starting in v6.3).  This driver is intended to interface to hardware running Xilinx (AMD) FPGAs with their proprietary PCIe IP.

Reference: [https://www.phoronix.com/news/AMD-Xilinx-XDMA-Linux-6.3](https://www.phoronix.com/news/AMD-Xilinx-XDMA-Linux-6.3)

I am trying to get this driver to run on my machine with a custom card (with a Xilinx FPGA).

My OS is: Linux 6.8.0-50-generic 22.04.3 - Ubuntu 

I can see the driver on the machine.  I have verified that my device is properly enumerating:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294514&stc=1[/IMG]

Note, at the bottom it states that "Kernel driver in use: xdma"  This is an older driver (from obtained from the Xilinx git repository) - from before the release in kernel v6.3.  When I unload this driver, I cannot get the kernel version to recognize/associate with my card.  Looking into the source code, I do not see a place where it stores supported vendorID/deviceID pairs (like the old driver did).  Am I missing something basic?  How can I get this driver to associate with my card?

I apologize if any of the above questions/information seems weird.  I am a hardware engineer out of his depth with Linux drivers...

---

### Post by 1fallen on 2024-11-14
The last I played with it, they wanted me to DL this: [https://jungo.com/windriver/?product=WinDriver#download](https://jungo.com/windriver/?product=WinDriver#download)

You may want to look at it, I did not try or use it's a PAID Or 30 Day Trial it was not worth it for me anyway.
Before you jump on that link here is the Quote:
> [evgeny.jungo]("https://adaptivesupport.amd.com/s/profile/0052E00000N33mKQAR") (Member)
6 years ago

Hello,
 
I saw your post and as it seems, you are having trouble with driver development for Linux I would like to offer you to try out our driver development toolkit - WinDriver.
 
WinDriver is a toolkit for PCI/USB devices for the OS's of Windows/Linux, that automatically generates a driver that is specific to your hardware. WinDriver provides a sample of our XDMA PCIe driver that you can try out.   The toolkit enables you to access your hardware and implement your device functionality, without having to develop in the kernel mode. For more information click here PCIe Online Demo [[https://www.youtube.com/watch?v=-o6M1ljZMQk](https://www.youtube.com/watch?v=-o6M1ljZMQk)].   In order to download WinDriver's free trial version please click here [[https://www.jungo.com/st/contact-form-2/?product=WinDriver](https://www.jungo.com/st/contact-form-2/?product=WinDriver)].    For more information please contact me via email: [EMAIL="evgenym@jungo.com"]evgenym@jungo.com[/EMAIL] or phone: 1-408-600-0851 ext.651   Best regards,    Evgeny Moss Account Manager  Jungo Connectivity Ltd  P:+1 408-600-0851 [tel:+1%20408-600-0851]  M:+1 408-351-6854 ext:651 [tel:+1%20408-351-6854] [EMAIL="evgenym@jungo.com"]evgenym@jungo.com[/EMAIL]




I'm running a Hybrid OS currently so I'm not much help on your current kernel.
```
[FONT=monospace][COLOR=#000000]lsmod | grep xdma [/COLOR]
xdma                   24576  0
####
[/FONT][FONT=monospace][COLOR=#000000]Linux tuxedo-os-btrfs 6.11.0-105009-tuxedo #9tuxnoble1 SMP PREEMPT_DYNAMIC Sat Oct 26 07:13:55 UTC 2024 x86_64[/COLOR]
 x86_64 x86_64 GNU/Linux

[/FONT]
```[FONT=monospace]

We have a few extra sharp Kernel testers as well, maybe one will pop in. 


[/FONT]

---

### Post by hobbss on 2024-11-14
Thank you for the response.  However, it was my understanding that by getting the driver officially released into the kernel, the result was users (like me) no longer had to scrimp/scrounge/roll our own drivers to interface to cards with Xilinx FPGAs - we simply use the [released] XDMA driver - which is now integrated into the kernel.

---

### Post by 1fallen on 2024-11-14
They Lied....LOL

Proof this is on Arch with tuned kernel (BORE)
```
[FONT=monospace][COLOR=#54FF54]**&#9492;&#9472;>**[/COLOR][COLOR=#000000] lsmod | grep xdma [/COLOR]
[COLOR=#54FF54]**&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>**[/COLOR]


[/FONT]
```[FONT=monospace]
As you see nothing there.
The one on Buntu flavors are very basic (Lacking Drivers)[/FONT]

Refer to this: [URL="https://github.com/Xilinx/dma_ip_drivers/tree/master/XDMA/linux-kernel"]https://github.com/Xilinx/dma_ip_drivers/tree/master/XDMA/linux-kernel


[/URL]

---

### Post by hobbss on 2024-11-14
Again, I appreciate your response.  Please don't interpret my continuing questions as challenging you (as previously mentioned, I am a hardware engineer, not a programmer).  The driver available at the Xilinx git repository you linked to is of... dubious quality, at best.  However, the one that should be in the kernel (see here: [linux/drivers/dma/xilinx/xdma.c at master · torvalds/linux · GitHub]("https://github.com/torvalds/linux/blob/master/drivers/dma/xilinx/xdma.c")) is supposed to be much better.  If I could get it to load properly...

Series of [potentially dumb] questions/observations:
1. When I was running an earlier kernel (6.2), I went out, got that driver from the Xilinx repo, compiled it and [sort of] used it.
2. When I upgraded to v6.8 kernel, I saw that the xdma code was already there (as in, I did NOT need to get it and add to the machine).
3. Even though the code for the driver is "in the kernel" do I still need to compile and load it?

---

### Post by 1fallen on 2024-11-14
> **hobbss said:**
> Again, I appreciate your response.  Please don't interpret my continuing questions as challenging you (as previously mentioned, I am a hardware engineer, not a programmer).  The driver available at the Xilinx git repository you linked to is of... dubious quality, at best.  However, the one that should be in the kernel (see here: [linux/drivers/dma/xilinx/xdma.c at master · torvalds/linux · GitHub]("https://github.com/torvalds/linux/blob/master/drivers/dma/xilinx/xdma.c")) is supposed to be much better.  If I could get it to load properly...

Nope I did not feel a challenge by you, just trying to save you time is all. I got ran around for about 4 hours trying to sort all this out. :)
> **hobbss said:**
> 
Series of [potentially dumb] questions/observations:

3. Even though the code for the driver is "in the kernel" do I still need to compile and load it?
Yes you will have to compile it.
Went rather smooth but Again I have no PCIE card here at all.
```
[FONT=monospace][COLOR=#000000]Error: The Kernel module installed correctly, but no devices were recognized.[/COLOR]
[/FONT]
```
They have a forum that, might be better suited for help there: [https://adaptivesupport.amd.com/s/question/0D54U00008CQkzHSAT/install-xdma-drivers-in-ubuntu-22042-lts?language=en_US](https://adaptivesupport.amd.com/s/question/0D54U00008CQkzHSAT/install-xdma-drivers-in-ubuntu-22042-lts?language=en_US)

---

### Post by hobbss on 2024-11-18
My software contractor has told me that this driver (in the kernel) is a "platform" driver, not a "device" driver, and is meant to target Xilinx SoC devices that are running Linux and have DMA engines in them (i.e., Zynq) rather than an actual PCie/DMA combo driver targeting a PCIe device (end point) in a larger system running Linux.  Does that make sense?  Is there a way I can verify that?

---

### Post by 1fallen on 2024-11-18
Platform devices are inherently not discoverable, i.e. the hardware cannot say "Hey! I'm present!" to the software. 
But yes It makes some sense:
Please check in apt:
```
[FONT=monospace][COLOR=#000000]apt search Xilinx [/COLOR]
Sorting... Done 
Full Text Search... Done 
[COLOR=#18B218]fpga-manager-xlnx[/COLOR][COLOR=#000000]/noble 2022.1ubuntu1 amd64 [/COLOR]
  Xilinx FPGA manager 

[COLOR=#18B218]libdfx-dev[/COLOR][COLOR=#000000]/noble 2023.2-0ubuntu4 amd64 [/COLOR]
  library to configure Programmable Logic on Xilinx FPGAs - development files 

[COLOR=#18B218]libdfx1.0[/COLOR][COLOR=#000000]/noble 2023.2-0ubuntu4 amd64 [/COLOR]
  library to configure Programmable Logic on Xilinx FPGAs - shared library 

[COLOR=#18B218]libfreesrp-dev[/COLOR][COLOR=#000000]/noble 0.3.0-5 amd64 [/COLOR]
  Software defined radio support for FreeSRP hardware (development files) 

[COLOR=#18B218]libfreesrp0[/COLOR][COLOR=#000000]/noble 0.3.0-5 amd64 [/COLOR]
  Software defined radio support for FreeSRP hardware (library) 

[COLOR=#18B218]libunilog-dev[/COLOR][COLOR=#000000]/noble 2.5-2build3 amd64 [/COLOR]
  wrapper library for google-glog (develop) 

[COLOR=#18B218]libunilog2[/COLOR][COLOR=#000000]/noble 2.5-2build3 amd64 [/COLOR]
  wrapper library for google-glog 

[COLOR=#18B218]libxrt-dev[/COLOR][COLOR=#000000]/noble 202210.2.13.466+dfsg-8ubuntu5 amd64 [/COLOR]
  Xilinx Runtime (XRT) - development files 

[COLOR=#18B218]libxrt-utils[/COLOR][COLOR=#000000]/noble 202210.2.13.466+dfsg-8ubuntu5 amd64 [/COLOR]
  Xilinx Runtime (XRT) - runtime -- utilities 

[COLOR=#18B218]libxrt1[/COLOR][COLOR=#000000]/noble 202210.2.13.466+dfsg-8ubuntu5 amd64 [/COLOR]
  Xilinx Runtime (XRT) - runtime libraries 

[COLOR=#18B218]linux-firmware-xilinx-ap1302[/COLOR][COLOR=#000000]/noble,noble 1:2.0-0ubuntu1 all [/COLOR]
  Firmware for the AP1302 ISP, for Xilinx boards 

[COLOR=#18B218]linux-firmware-xilinx-vcu[/COLOR][COLOR=#000000]/noble,noble 2020.2-0ubuntu1 all [/COLOR]
  Xilinx VCU firmware files 

[COLOR=#18B218]linux-xilinx-headers-6.8.0-1008[/COLOR][COLOR=#000000]/noble-updates,noble-updates,noble-security,noble-security 6.8.0-1008.9 all [/COLOR]
  Header files related to Linux kernel version 6.8.0 

[COLOR=#18B218]linux-xilinx-tools-common[/COLOR][COLOR=#000000]/noble-updates,noble-updates,noble-security,noble-security 6.8.0-1008.9 all [/COLOR]
  Linux kernel version specific tools for version 6.8.0 

[COLOR=#18B218]linux-xilinx-tools-host[/COLOR][COLOR=#000000]/noble-updates,noble-updates,noble-security,noble-security 6.8.0-1008.9 all [/COLOR]
  Linux kernel VM host tools 

[COLOR=#18B218]openfpgaloader[/COLOR][COLOR=#000000]/noble 0.12.0-1 amd64 [/COLOR]
  Universal utility for programming FPGAs 

[COLOR=#18B218]xc3sprog[/COLOR][COLOR=#000000]/noble 0+svn795+dfsg-4 amd64 [/COLOR]
  JTAG flashing tool for FPGAs, CPLDs and EEPROMs 

[COLOR=#18B218]xilinx-bootgen[/COLOR][COLOR=#000000]/noble 2022.2-2ubuntu3 amd64 [/COLOR]
  boot image converter for Xilinx ARM SoCs 

```
Also run through this list:
```
[/FONT][FONT=monospace][COLOR=#000000]apt search Zynq [/COLOR]
Sorting... Done 
Full Text Search... Done 
[COLOR=#18B218]fpga-manager-xlnx[/COLOR][COLOR=#000000]/noble 2022.1ubuntu1 amd64 [/COLOR]
  Xilinx FPGA manager 

[COLOR=#18B218]libxrt-dev[/COLOR][COLOR=#000000]/noble 202210.2.13.466+dfsg-8ubuntu5 amd64 [/COLOR]
  Xilinx Runtime (XRT) - development files 

[COLOR=#18B218]libxrt-utils[/COLOR][COLOR=#000000]/noble 202210.2.13.466+dfsg-8ubuntu5 amd64 [/COLOR]
  Xilinx Runtime (XRT) - runtime -- utilities 

[COLOR=#18B218]libxrt1[/COLOR][COLOR=#000000]/noble 202210.2.13.466+dfsg-8ubuntu5 amd64 [/COLOR]
  Xilinx Runtime (XRT) - runtime libraries 

[COLOR=#18B218]xilinx-bootgen[/COLOR][COLOR=#000000]/noble 2022.2-2ubuntu3 amd64 [/COLOR]
  boot image converter for Xilinx ARM SoCs

```

[/FONT]
[FONT=monospace]I have no Idea which you will need though or how old they are. Whithout me having that card physically attached to my machine...I'm shooting in the dark.[/FONT]

---

