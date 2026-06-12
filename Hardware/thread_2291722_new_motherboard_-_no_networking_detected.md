---
title: "new motherboard - no networking detected?"
date: 2015-08-22
forum: Hardware
---

### Post by blm14 on 2015-08-22
First time for everything. Motherboard failure after several years of headless ubuntu applicances. This one running 14.04LTS kernel 3.13.0-62

Old mobo: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813128597&cm_re=gigabyte_ga-e350n-_-13-128-597-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128597&cm_re=gigabyte_ga-e350n-_-13-128-597-_-Product)

New mobo: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813130759](http://www.newegg.com/Product/Product.aspx?Item=N82E16813130759)

Figured the same processor architecture should be helpful. It boots, video everything works, but they have different ethernet chipsets. The new motherboard only sees the loopback interface from ifconfig, AND I've already tried a USB ethernet controller as well as a mini wifi usb NIC.

The new board's wifi chipset is [COLOR=#4D4D4D][FONT=helvetica]Realtek 8111G. I rather stupidly never got around to installing build-essential or the kernel source prior to when the old mobo died, so I can't compile the r8168 kernel driver myself and depmod it in. Any thoughts on how to fix this?

dmesg: [/FONT][/COLOR]http://pastebin.com/ZNmxuQiC

lspci:
```

00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8400]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 9840
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 0
00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 01)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 39)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 39)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 3a)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 02)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 5
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)

```

/etc/networking/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet dhcp

```

output from ifconfig:
```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:208 errors:0 dropped:0 overruns:0 frame:0
          TX packets:208 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15632 (15.6 KB)  TX bytes:15632 (15.6 KB)

```

Any help appreciated. TIA

---

### Post by weatherman2 on 2015-08-22
Assuming this is the same Ubuntu installation, the new network card is probably being detected as eth1.  (And eth2, eth3, etc. as you add/try new devices.)  So "auto eth0" doesn't do anything.

The easiest thing to do is get rid of the record of your old network card - erase this file:

```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```

then reboot - now eth0 will be assigned to your new network card (and the above file will be automatically re-generated).

---

### Post by Joe_Aquilina on 2015-11-26
Hello, after replacing an old motherboard in a machine here (running Ubuntu 14.04 LTS), I seem to be having exactly the same problem. My hardware (old and new) is different but the behaviour is the same. Having checked the /etc/udev/rules.d/70-persistent-net.rules file, the new network card did not appear to be detected as eth1. It appeared to not be detected at all.

As suggested above by weatherman2, I deleted the file and rebooted. Now I have no /etc/udev/rules.d/70-persistent-net.rules file and eth0 is still not being detected. It seem that there is some other problem which I haven't found yet. I am not experienced enough to know where else to look and/or how to fix the problem.

Any suggestions? And is there any information that you might need to help diagnose and fix this?

Thanks in advance.

---

### Post by Joe_Aquilina on 2015-11-26
Investigating further, I have found the e1000e drivers on Sourceforge, which I have downloaded and installed. I now have network connectivity. Still no internet connectivity on that machine though so it seems I still have some further detective work to do to fix that.

---

