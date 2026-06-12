---
title: "[SOLVED] Wifi?"
date: 2008-09-04
forum: General Help
---

### Post by Yezinki on 2008-09-04
Ubuntu does not connect via wireless lan...displays error .....in DOS mode like.....go to linuxwireless.org....install firmware version 4??

[http://grouper.ieee.org/groups/802/11/](http://grouper.ieee.org/groups/802/11/)

Which driver should I install for Sony Vaio VGC-LS1?

Regards!

---

### Post by porchrat on 2008-09-04
use this command to find out which card you are running:

```
lshw -C network
```

---

### Post by Yezinki on 2008-09-04
ubuntu@ubuntu-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:13:a9:4b:18:f6
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=10.0.0.4 latency=0 module=sky2 multicast=yes
  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:cf:12:c4:02
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
ubuntu@ubuntu-desktop:~$ 
ubuntu@ubuntu-desktop:~$

---

### Post by porchrat on 2008-09-04
This is your wireless card:

Broadcom Corporation BCM4311

You need the linux driver for that card...google it...you could also use the windows driver by installing ndiswrapper...just search the forum there r THOUSANDS of threads on this subject...mainly the Atheros and Broadcom cards so you have plenty of guides

Here is an example (a little outdated but it might still work)

[http://ubuntuforums.org/showthread.php?t=185174]("http://ubuntuforums.org/showthread.php?t=185174")

---

### Post by Peter09 on 2008-09-04
These drivers are in the repository. Goto synaptic and do a search on BCM4xx, you'll find the packages there.

---

### Post by Yezinki on 2008-09-04
Their aint any??

---

### Post by Peter09 on 2008-09-04
sorry that should be bcm43

try

```
sudo apt-get install b43-fwcutter
```

---

### Post by Yezinki on 2008-09-04
ubuntu@ubuntu-desktop:~$ sudo apt-get install b43-fwcutter
[sudo] password for ubuntu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu-desktop:~$ 
ubuntu@ubuntu-desktop:~$

---

### Post by Peter09 on 2008-09-04
So you already have the drivers.
Please do

```
ifconfig
```

and post the resulting output.

---

### Post by Yezinki on 2008-09-04
ubuntu@ubuntu-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:a9:4b:18:f6  
          inet addr:10.0.0.4  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:a9ff:fe4b:18f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1713 errors:0 dropped:0 overruns:0 frame:0
          TX packets:981 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1110771 (1.0 MB)  TX bytes:225626 (220.3 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1674 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1674 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:83700 (81.7 KB)  TX bytes:83700 (81.7 KB)

ubuntu@ubuntu-desktop:~$ 
ubuntu@ubuntu-desktop:~$

---

### Post by biggest lund on 2008-09-04
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by Peter09 on 2008-09-04
have had another look at your lshw output. It shows that your netwrok is DISABLED. I think this refers to the hardware switch somewhere on the laptop. Can you check if that is on or off.

---

### Post by Yezinki on 2008-09-04
Both Enabled but wont connect.

Thanks!

---

### Post by falcon61102 on 2008-09-04
Have you tried loading the module manually with:
```
sudo modprobe bcm43xx
```

Then reboot.

---

