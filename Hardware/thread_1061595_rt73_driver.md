---
title: "rt73 driver"
date: 2009-02-06
forum: Hardware
---

### Post by maitrebart on 2009-02-06
I have a dlink dwl-g122 (c1) and I followed the setup instructions as per [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236) .

However, the network interface still does not work. According to [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495) , if "lshw -C network" reports no driver on the configuration line, then there is a problem with the installation.

The output of the above command should look like this:

> *-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       logical name: wlan0
       version: 03
       serial: 00:12:17:35:17:10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lsbcmnds driverversion=1.48rc1+Cisco-Linksys ,LLC.,02/1 ip=192.168.1.101 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c001fff irq:11

However mine looks like:

>  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:17:9a:d1:34:32
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.104 multicast=yes wireless=RT73 WLAN

Looks like the network interface has no driver associated to it though I followed the very precise installation procedure described in the first link.

I guess this is why I have the following output for the iwconfig command:

> wlan0     RT73 WLAN  ESSID:""  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

When I boot, I see a light flashing for 1 second and flahsing again after 2 or 3 seconds.

I know the driver is loaded since "lsmod | grep rt73" gives:

> rt73                  216192  1 
usbcore               146412  6 rt73,usb_storage,libusual,ehci_hcd,ohci_hcd

I guess the problem I have is that the network interface was not able to link to the rt73 driver.

I hope someone can help me!

Thanks

---

### Post by maitrebart on 2009-02-21
Apparently, even if if "lshw -C network" reports no driver on the configuration line, it can still work.

Look at end of this thread for the solution:

[http://ubuntuforums.org/showthread.php?p=6775089]("http://ubuntuforums.org/showthread.php?p=6775089")

---

### Post by ProNux on 2009-02-24
My RT-73-based WLAN is working well using the native driver from Ralink website.  I have Edimax EW-7318USg.  I didn't use the serialmonkey/ndiswrapper.  I just followed carefully the README file inside the archive.

By the way, I have a past problem on the one - unstable Rt-73 connection, but the cause was WLAN conflict.  I have 2 WLANs (one built-in on my laptop, then this RT-73 wlan).  What I did was just disable the built-in and solved my problem.

---

### Post by maitrebart on 2009-02-24
> **ProNux said:**
> [...] By the way, I have a past problem on the one - unstable Rt-73 connection, but the cause was WLAN conflict.  I have 2 WLANs (one built-in on my laptop, then this RT-73 wlan).  What I did was just disable the built-in and solved my problem.

I have 1 wlan and 1 eth. I un-dhcp the eth one when booting (/etc/rc.local).

---

### Post by cariboo on 2009-02-24
I just plugged my rt73 usb device in and it worked out of the box. 

From the output of lshw it looks like you got an ip address. Just as a test I would suggest turning off all security and try to connect to an open ap.

Jim

---

### Post by ProNux on 2009-02-25
Also, I tried running live Ubuntu 8.1 Intrepid Ibex and got my RT-73 working out-of-the-box.

---

### Post by maitrebart on 2009-02-25
> **cariboo907 said:**
> I just plugged my rt73 usb device in and it worked out of the box. 


Do you have a dwl-g122 (c1) ?

---

### Post by maitrebart on 2009-02-25
> **ProNux said:**
> Also, I tried running live Ubuntu 8.1 Intrepid Ibex and got my RT-73 working out-of-the-box.

Do you have a dwl-g122 (c1) ?

---

### Post by ProNux on 2009-02-27
Bro, here is the link to download the driver.  I found out that it is similar to my driver (except the version).

[http://www.dlink.com.ph/products/support.asp?sec=&pid=346#drivers](http://www.dlink.com.ph/products/support.asp?sec=&pid=346#drivers)


For kernel version 2.6.27
[http://www.ralinktech.com.tw/data/drivers/2009_0206_RT73_Linux_STA_Drv1.1.0.2.tar.bz2](http://www.ralinktech.com.tw/data/drivers/2009_0206_RT73_Linux_STA_Drv1.1.0.2.tar.bz2)


This example is for the first link but almost similar instructions.

Download G122_Linux_Driver.tar.gz.
Extract the folder inside (RT73_Linux_STA_Drv_1.0.2.0) to your desktop (or any location)

Open the extracted folder and follow the instructions carefully on the README file.

Take note of these.

Step 2.  --> It depends on what kernel version you have.
Step 3.  --> For kernel 2.4 only
Step 5.  --> MAKE a directory  **etc/Wireless/RT73STA** beforehand before you can follow the step 5 instruction.
           

Good luck.

---

### Post by ProNux on 2009-02-27
> **maitrebart said:**
> Do you have a dwl-g122 (c1) ?

No, I got Edimax EW-7318USg, BUT they have the same chipset (RT-73).

---

