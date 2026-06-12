---
title: "Problem installing nvidia driver"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by jlbr21 on 2009-05-01
Hi,
I upgraded from 8.10 to Jaunty, well, i have many issues, especially, the nvidia driver is giving me a headache. OK, this is the problem. After upgrading, i disabled the driver, and then tried to install it again, that did not work since there is a bug with the jockeygtk application which controls the downloading of the driver. SO then I go and download the driver from the nvidia page, I try to install it by running "sudo sh NVIDIA-Linux-x86_64-180.51-pkg2.run" and i get an error saying i am running an X server and tehrefore cannot install the driver.

Well, i dont know how to disable the x server and install the nvidia driver.

Can somebody help me?

Thanks.

---

### Post by inobe on 2009-05-01
jlbr21 lets troubleshoot this without manually installing the driver.

first open terminal and type

```
lspci
```

copy the output and paste it on the board.


also open synaptic and search **nvidia**

tell me if each of these components are installed.

[IMG]http://www.itsyourpc.org/duane/files/nvidia_installed.jpg[/IMG]

---

### Post by jlbr21 on 2009-05-01
Hello Inobe,

The output when running lspci:

juanluis@juanluis-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
06:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller
06:00.1 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
06:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
06:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
06:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
juanluis@juanluis-laptop:~$ 


I'm also attaching a screenshot where you can see all the nvidia related packages installed.

Thanks for your help!

---

### Post by inobe on 2009-05-01
looks like you have the required components so were good there.


your card is being properly detected as well.


when you activate the 180.44 driver in "hardware drivers" what happens exactly ?


also when you go to system> administration> nvidia settings' does it produce an error.

---

### Post by jlbr21 on 2009-05-01
Thanks for the help but I have been doing some research into Intel graphic cards and jaunty jackalope and it seems they just don't get along and there are a number of bugs to be fixed.

For now i managed to solve some issues, the driver is now installed and running half OK. Took me all day but getting there.

I've still got a problem with compiz, but same thing, its a bug that canonical should fix sometime in the future.

Thanks inobe!

---

