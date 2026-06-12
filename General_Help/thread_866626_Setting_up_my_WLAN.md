---
title: "Setting up my WLAN"
date: 2008-07-22
forum: General Help
---

### Post by zeke13 on 2008-07-22
I am completely new to Linux, I just installed wubi v8.04.1 on a dedicated partition. How do I get wubi to recognize my Wireless LAN? Also, how do I access the partition where all my data is located?

---

### Post by ago on 2008-07-22
The data is under /host
As for the network you should ask that in the networking forum: [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

---

### Post by nwubie on 2008-07-23
**ago** answered your question about finding your system partition in Ubuntu. If you have other drives or partitions you'll need to mount them before you can access them. Easiest way is to run nautilus (type nautilus in a terminal) and click your drive/partition in the left pane (first click will mount it, second click will access it). You can mount them automatically at startup if you wish, just ask.


**About the WLAN :**

First make sure the default wireless drivers really don't work. Type iwconfig. Do you see any wlan0 entry there ?

Go to System -> Administration -> Network. Click on unlock. Select the wireless connection if it's there, tick it if it's unticked, click on properties and see if you can browse through the various ESSID's (= the names of the wireless network you can access). If you can then the default driver works fine, just enter your encryption key and select your network.

If the default driver doesn't work with your wireless adapter or if you can't see any wireless connection you can use ndiswrapper and the Windows drivers.

First thing is to get the .inf and .sys files that are the drivers for your network adapter. If you're lucky those files will be available directly on the CD that came with your wireless adapter (pick the 32bit version if this is the 32bit version of Ubuntu). If you can't find them there then download them from here : [http://www.linuxant.com/driverloader/drivers.php](http://www.linuxant.com/driverloader/drivers.php). You can also take them out of your windows installation by looking the name of the driver that's currently used for your network adapter in the device manager and searching the system drive for those drivers (.inf and .sys files).

Back in Ubuntu

Go to synaptic, make sure you enabled the main, multiverse, restricted and universe repositories, and search for ndiswrapper. Install ndiswrapper-common and ndiswrapper-utils-1.9.

If you have no internet access then download those 2 packages under Windows :
[http://packages.ubuntu.com/hardy/all/ndiswrapper-common/download](http://packages.ubuntu.com/hardy/all/ndiswrapper-common/download)
[http://packages.ubuntu.com/hardy/i386/ndiswrapper-utils-1.9/download](http://packages.ubuntu.com/hardy/i386/ndiswrapper-utils-1.9/download)
Back in ubuntu copy them to your user folder and install them by typing :
**sudo dpkg -i ndiswrapper*.deb**

Copy the XP drivers (the .inf and .sys files you just found) to your user folder in Ubuntu and type
**sudo ndiswrapper-1.9 -i driver_name.inf** 
(replacing driver_name by the corresponding name)

Verify that the driver is loaded properly in ndiswrapper :
**ndiswrapper -l**
As a result you should get :
[b]Installed ndis drivers:
(driver_name) driver present, hardware present[/b]

Then you'll need to unload the default driver. First thing is to find out what driver you need to unload. If your adapter is a PCI card then type
**sudo lspci** 
to get a listing of all pci cards (if it's an USB adapter type sudo lsusb). Find the entry that corresponds to your wireless interface and write down the name you'll see next to driver=

Then type
**lsmod**
to find the name of the related module (can differ a little from the driver's name) and unload that module :
**sudo modprobe -r name_of_the_default_module**

Type
[b]sudo ndiswrapper -m
sudo modprobe ndiswrapper[/b]
to create the ndiswrapper module and load it

type
**iwconfig**
and check that you see a wlan0 entry now.

You should now be able to configure it using System => Administration => Network.

To load all those settings at startup you'll need to blacklist the default module and load ndiswrapper automatically. Only do this once you've made sure that your wireless adapter is working properly and that you can surf the web with it. Note that blacklisting the default module can be tricky if it's the b43 or b44 module because of an issue with the ssb module. If that's the case report here. Else type the following lines : 
**echo "blacklist name_of_the_default_module"|sudo tee -a /etc/modprobe.d/blacklist**
**echo "ndiswrapper"|sudo tee -a /etc/modules**
and restart Ubuntu.

---

