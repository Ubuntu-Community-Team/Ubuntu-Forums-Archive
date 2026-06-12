---
title: "Bluetooth: Ralink corp. Device 3298 not working in Ubuntu 12.10"
date: 2013-02-17
forum: Hardware
---

### Post by sulekhadahiya on 2013-02-17
My new laptop has Bluetooth Ralink corp. Device 3298 and it is not detected by ubuntu. 
> HP-Pavilion-g6-Notebook-PC:~$ rfkill list
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no


After enabling the Bluetooth:
> HP-Pavilion-g6-Notebook-PC:~$ rfkill list
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no

Still in bluetooth settings it shows "bluetooth is disabled".

> HP-Pavilion-g6-Notebook-PC:~$ lsusb | grep -i bluetooth
HP-Pavilion-g6-Notebook-PC:~$

The above command shows nothing.
Is there any solution for it.

---

### Post by laca2 on 2013-03-28
**Bluetooth: Ralink corp. Device 3298 not working in Ubuntu 12.04 either.** 

Upgrading the kernel [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8.4-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8.4-raring/) makes the wireless connection work, but still no bluetooth connectivity. 
My laptop, is listed as certified for Ubuntu ([http://www.ubuntu.com/certification/hardware/201209-11728/components/](http://www.ubuntu.com/certification/hardware/201209-11728/components/)). 
Also tried to install the RT3290 PCIe  driver package and firmware available at the manufacturer's site ([http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501](http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501)) but that driver keeps crashing the system.

Are there any plans to support the Ralink 3298 device in the near future? (googling after it gives no result) Could anyone point me to the relevant project page, if any?

Thanks,
laca

---

### Post by laca2 on 2013-03-28
Just found [this]("http://ubuntuforums.org/showthread.php?t=2115570&p=12507896#post12507896") post for a potential solution. I'll try that and come back with the results...

---

### Post by josue-soto1 on 2013-09-23
Hi I had installed 12.04LTS 64 bit.
Drivers for WIFI works fine. However Bluetooth is not detected. 
I had tried solution: Setting Up Wifi and Bluetooth on 12.04 LTS posted previously, but cannot compile in the latest kernel 3.8. 

regards
Josue Soto

---

