---
title: "Realtek 8168 under Ubuntu 8.10"
date: 2008-12-26
forum: Hardware
---

### Post by emeraldchen on 2008-12-26
Hi and sorry for my bad english ;-)

I have a Asus G50V Laptop with a Realtek RTL8168B network interface. After spent a lot of time, i manged to use the Laptop with Ubuntu 8.04 (custom Kernel 2.6.27-7). To use the network interface, Everything worked but not very stable. To use the network interface I had to replace the driver from Ubuntu with the original driver from Realtek.

Now I tried to change from Ubuntu 8.04 (64-bit) to  Ubuntu 8.10 (64-bit). It works much better and nearly everything worked out of the box. The only thing that dont't work, is the network card.

I tried nearly anything (replacing driver by the Realtek driver, disabling wireless drivers, compiling the new kernel 2.6-28 ) but nothing worked.
The network device shows always the same behaviour:
Wen I configure DHCP to get the ip, the network manager tries to get the ip but then it says that there is no network connection. When I type in a fix ip adress, there is no error, but the network doesn't work.

I've also tried to shut down the network manager and set up the ethernet device manually with "ifconfig eth0 192.168.1.1". The result was "SIOCSIFADDR: No buffer space available".

This is my System :

Core2 Duo CPU P8600 @ 2.40GHz
4GB DDR2 800MHz
NVIDIA GeForce 9700M GT 512MB
15.4&#8243; @ 1680×1050
Realtek 8168B Gigabit Ethernet
Intel WiFi Link 5100 802.11abgn Wireless card
Intel ICH9 sound card with Realtek ALC663 codec
6 cell battery for up to 2 hours of autonomy
320GB WD hard disk 

"lspci | grep Ethernet" :

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

eth0 part of "ifconfig" :

eth0      Link encap:Ethernet  HWaddr 00:22:15:90:08:a2  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1300 (1.3 KB)  TX bytes:1884 (1.8 KB)
          Interrupt:249

---

### Post by nausicaavow on 2008-12-26
I just posted a walk-through on how to fix this. I had the same problem.
[http://ubuntuforums.org/showthread.php?p=6441406#post6441406]("http://ubuntuforums.org/showthread.php?p=6441406#post6441406")

---

### Post by emeraldchen on 2008-12-27
Hi, thanks for your post.

Unfortunately the problem still exists. But I just found out that the network manager of ubuntu has a bug. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284377]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284377") When uncheck the network manager in system->preferences->sessions, the network interface works perfectly.

Maybe the only way is to hope for a patch which solves the problem.. :-(

best regards

---

### Post by avilella on 2009-04-13
[http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)

If you have access to any of the laptops below and have tried to run Linux, please take a moment to provide the DSDT information for the laptop in this link:

[http://bugs.launchpad.net/bugs/312756](http://bugs.launchpad.net/bugs/312756)

Sony Vaio Z-series (intel/nvidia)
Fujitsu Siemens Amilo XI 3650 (intel/nvidia)
BenQ Joybook S42 (intel/nvidia)
ASUS N10J (intel/nvidia)
Dell Studio XPS 13 (nvidia/nvidia)
ASUS Intros G71Gx (?/nvidia GeForce 260M)
MSI GT628 (?/nvidia GeForce 160M)
LG Xnote P510 Laptop (?/nvidia GeForce GT 130M)
HP HDX 18t (?/nvidia GeForce GT 130M)
Dell XPS M1730 (nvidia/nvidia)
MSI EX630 (nvidia/nvidia -- )
Toshiba Qosmio X305-Q706/Q708 (nvidia/nvidia -- 9400m + 2x9800m GTS)
Acer Aspire 7530 (nvidia/nvidia -- 9100M G + GeForce 9300M GS)
ASUS X83Vm-X1 (?/nvidia)
+ Clevo M860TU (?/nvidia GeForce 9800M GTS)
+ Acer Aspire 8930G (?/nvidia GeForce 9700M GT)
+ Asus G50V (?/nvidia GeForce 9700M GT)
Lenovo ThinkPad T500 (intel/ati)
Lenovo ThinkPad T400 (intel/ati)
ASUS M51Ta (intel/ati)
Fujitsu-Siemens Amilo Sa 3650 (intel/ati)
MSI PX211 12'' (intel/ati)
HP Pavilion tx2500 (intel/ati)

To compile your DSDT information, install if you haven't already the acpidump and iasl tools:
sudo apt-get install acpidump iasl           # on Debian-based systems

Then run the following commands:

sudo acpidump > acpidump.txt
sudo acpixtract acpidump.txt
iasl -d DSDT.dat

This will create a DSDT.dsl file that you can attach to the bug report. This information will allow the developers to fully implement the hybrid graphics features for Linux.

---

