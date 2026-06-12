---
title: "USB wireless adapter install"
date: 2008-02-19
forum: Hardware &amp; Laptops
---

### Post by noMS4me on 2008-02-19
Greetings All!

I have been trying to install drivers on a desktop running Ubuntu 7.10 for a Pluscom WU-ZD1211B Wireless USB Adapter with no success but with quite a bit of education.

Can someone please lead me by the hand on this one because at this point I am pretty much lost... Thanks!!!  Steve

These are the instuctions (which might as well be in another language) and I have the drivers on a cd: (I have not been able to figure out how to access to even begin to extract file):confused:

Driver Installation Guide for ZD1211 wireless adapter in Linux
It needs only a few steps to build and install the driver we provided. Before you begin tobuild the driver, make sure (1) Kernel Source Tree is installed in your Linux system;(2) Kernel wireless function (IEEE 802.11) is available.

Step 1: Package Extraction
Type this command: tar zxvf ZD1211LnxDrv_2_21_0_0.tar.gz
The purpose of this step is to extract this package by tar. After extracting this package,
you can see the source files. You should change directory into this directory for
proceeding the next step.

Step 2: Compile the driver
You just need to type the command “make”, and the driver module will be generated and
installed.

Step 3: Load the driver
Use the command “modprobe –i zd1211b” to load the driver. In order to check whether
the driver is loaded successfully, you can use the command “lsmod” for this check. If the
driver is loaded successfully, the following messages should be seen
...
zd1211 183576 0 (unused)
...
Please note that the number 183576 may vary in different systems.

Step 4: Configure the Wireless settings
Use the command “ifconfig” command to check the configurations, you can find ethX(If there is already an Ethernet adapter exits it may be eth0,and the adapteryou just installed may be eth1 ,and so on). Then type in the command “iwconfig eth1 essid xxx” where “xxx” is the SSID of your router. The adapter will connect the router automatically. Of course, make sure the router’s DHCP is enabled, Otherwise,
you should set the IP address of the adapter manually.

---

