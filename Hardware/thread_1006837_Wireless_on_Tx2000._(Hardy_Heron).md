---
title: "Wireless on Tx2000. (Hardy Heron)"
date: 2008-12-09
forum: Hardware
---

### Post by rusty spork on 2008-12-09
I am trying to get wireless working on my tx2000 with ubuntu hardy heron.   I have had it working on this tablet before, but I can't seem to get it working (nothing different than a fresh install), even with the same guide I used the first time ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)).  

Here is everything I have gotten from my terminal:


[HTML]joe@rusty:~$ echo -e 'blacklist bcm43xx\nblacklist wl' | sudo tee -a /etc/modprobe.d/blacklist
blacklist bcm43xx
blacklist wl
joe@rusty:~$ sudo apt-get install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-utils-1.9 is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19 linux-headers-2.6.24-19-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
joe@rusty:~$ mkdir ~/bcm43xx; cd ~/bcm43xx
mkdir: cannot create directory `/home/joe/bcm43xx': File exists
joe@rusty:~/bcm43xx$ wget http://myspamb8.googlepages.com/R151517-pruned.zip
--19:05:42--  http://myspamb8.googlepages.com/R151517-pruned.zip
           => `R151517-pruned.zip.2'
Resolving myspamb8.googlepages.com... 74.125.47.118
Connecting to myspamb8.googlepages.com|74.125.47.118|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 730,544 (713K) [application/octet-stream]

100%[====================================>] 730,544      627.66K/s             

19:05:44 (625.96 KB/s) - `R151517-pruned.zip.2' saved [730544/730544]

joe@rusty:~/bcm43xx$ unzip R151517-pruned.zip
Archive:  R151517-pruned.zip
replace bcm43xx.cat? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: bcm43xx.cat             
replace bcm43xx64.cat? [y]es, [n]o, [A]ll, [N]one, [r]ename: y 
  inflating: bcm43xx64.cat           
replace bcmwl5.inf? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: bcmwl5.inf              
replace bcmwl5.sys? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: bcmwl5.sys              
replace bcmwl564.sys? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: bcmwl564.sys            
joe@rusty:~/bcm43xx$ sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
joe@rusty:~/bcm43xx$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4328) present
joe@rusty:~/bcm43xx$ sudo depmod -a
joe@rusty:~/bcm43xx$ sudo modprobe ndiswrapper
joe@rusty:~/bcm43xx$ sudo cp /etc/network/interfaces /etc/network/interfaces.orig
joe@rusty:~/bcm43xx$ echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
auto lo
iface lo inet loopback

joe@rusty:~/bcm43xx$ sudo ndiswrapper -m
module configuration already contains alias directive

joe@rusty:~/bcm43xx$ echo 'ndiswrapper' | sudo tee -a /etc/modules
ndiswrapper
joe@rusty:~/bcm43xx$ echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
ENABLED=0
joe@rusty:~/bcm43xx$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 03
       serial: 00:21:00:0d:dd:0d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
joe@rusty:~/bcm43xx$ 
joe@rusty:~/bcm43xx$ 
[/HTML]

It shows that module=ndiswrapper; just like the guide says it should, and that if it says this, the wireless should start working, but it isn't doing anything different from when I installed ubuntu.


Thanks for any help you might be able to offer.


EDIT: It seems to be working after a reboot, but I can't find more than one network at a time, and I can't find my schools wireless (I can always see it in vista).

---

### Post by Favux on 2008-12-17
Hi rusty spork,

I have a TX2000 also.  Not what you want to hear, I'm sure, but I had no problem with wireless in Hardy once I went to the proprietary Broadcom STA wireless driver in Hardware Drivers.  It's also called "wl" in OSS.

Good luck.

---

