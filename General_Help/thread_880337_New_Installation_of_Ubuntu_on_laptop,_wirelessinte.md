---
title: "New Installation of Ubuntu on laptop, wireless/internet connectivity assistance"
date: 2008-08-04
forum: General Help
---

### Post by bizdcrawl on 2008-08-04
Ummm...... This is a double post. I posted this at Installation/Upgrades forum aswell with the same title. Sorry about getting impatient. But sadly, I am impatient because I am a little too excited that I installed ubuntu/linux(n00b) as a dual boot on my laptop and I want to play around with it. Butt...as the title says, I cant connect to internet. That just takes away the fun. 

So I will be grateful if anyone can direct me to the right link or the site to get me started.

Anyways, the problem I am having is, my laptop cant connect to internet. As I said this is my first time experiencing Ubuntu.

Here is what "sudo lshw -C network" gave me.

> *-network
description: Ethernet interface
product: NetLink BCM5787M Gigabit Ethernet PCI Express
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:10:00.0
logical name: eth0
version: 02
serial: 00:1a:4b:8d:59:bd
size: 100MB/s
capacity: 1GB/s
width: 64 bits
clock: 33MHz
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full latency=0 link=no module=tg3 multicast=yes port=twisted pair speed=100MB/s
*-network
description: Network controller
product: BCM4312 802.11a/b/g
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:30:00.0
version: 02
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=b43-pci-bridge latency=0 module=ssb
*-network DISABLED
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:00:00:1a:73:e3
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

so...Do I have the required drivers and its not recognizing the wireless connections or do I not have the drivers at all?

My initial guess was that I did not have the drivers.Then I came across 
[https://help.ubuntu.com/7.10/internet/C/ndiswrapper.html](https://help.ubuntu.com/7.10/internet/C/ndiswrapper.html) So, I googled my card model and got this link: [http://hardware4linux.info/component/18799/](http://hardware4linux.info/component/18799/)
Now thats where I am at. 

Am I in the right direction? If anyone can help me guide in the right path that would be awesomely helpful. 

Thank You.

---

### Post by cdtech on 2008-08-04
You are in the right direction. What do you get with "iwconfig". You may need the "ndiswrapper" using the windows driver. Using "ndiswrapper -l" will list the driver if installed via ndiswrapper.

---

### Post by mb_webguy on 2008-08-04
It looks like you need to use the Windows driver and ndiswrapper.  Since you're doing a dual boot, this should be fairly easy since you already have the Windows driver on the Windows partition.

First, install ndiswrapper (and a nifty GUI for it) by typing "sudo apt-get install ndisgtk".

Now locate the Windows driver for your wireless card.  It might be easier to do this in Windows, since you can go to Device Manager.  Once you've located the driver (the .inf file), type "gksu /usr/sbin/ndisgtk" in the terminal or select "Windows Wireless Drivers" from the System->Administration menu.  Click "Install New Driver", and select your Windows driver.

You may have to reboot at this point, but afterward you should be able to access wireless networks.

---

### Post by bizdcrawl on 2008-08-04
hey awesome people,

My stupid laptop says that it couldnt find the package ndisgtk when i tried the sudo apt-get intall ndisgtk. :(

---

### Post by cdtech on 2008-08-04
Just stick with the synaptic package manager for now and install the "ndiswrapper" and follow the instructions for installing the driver.

---

### Post by bizdcrawl on 2008-08-04
> **cdtech said:**
> Just stick with the synaptic package manager for now and install the "ndiswrapper" and follow the instructions for installing the driver.

But it needs the internet to actually get these packages. Gets me back to square one.

---

### Post by bizdcrawl on 2008-08-04
could this be a solution? 

[http://ubuntuforums.org/showthread.php?t=257840](http://ubuntuforums.org/showthread.php?t=257840)

---

### Post by mb_webguy on 2008-08-04
Yes, you need an internet connection in order to install packages.  Just get a network cable and use a wired connection.  

If you didn't have an active network connection when you installed Ubuntu, you probably have a hundred or so updates waiting for you, too...

---

### Post by cdtech on 2008-08-04
You can't use a wired Ethernet connection?

---

### Post by bizdcrawl on 2008-08-05
hey everybody,

sorry for the delay in responding. I followed the directions as noted above and got my wireless card working.

I first navigated to the windows folder and located the .inf driver file associated with my wireless card. Then I went to SYstem-Administration-Hardware drivers and the driver was available for me to install. After it was done and rebooted, it showed me the available networks and I connected without any hassle.

Thank you once again for all the assistance.

---

