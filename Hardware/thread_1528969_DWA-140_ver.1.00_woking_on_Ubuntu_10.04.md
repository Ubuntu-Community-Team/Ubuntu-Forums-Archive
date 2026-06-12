---
title: "DWA-140 ver.1.00 woking on Ubuntu 10.04?"
date: 2010-07-11
forum: Hardware
---

### Post by lajlev on 2010-07-11
Can't seem to get my lovely USB network adaptor working!
Been trying to following this tut [http://sudosys.be/?q=D-Link_DWA_140_ubuntu](http://sudosys.be/?q=D-Link_DWA_140_ubuntu) without any luck.

Anyone having luck with running it on ubuntu 10.04?

---

### Post by lajlev on 2010-07-12
This tutorial help me through :popcorn::

Determining which module you should use:

If a USB WiFi adapter is automatically detected by rt2870sta, rt3070sta or an rt2x00 module, it has likely been verified to function by that module's developers. While the rt2x00 driver has some support for rt2870 chipsets, it seems that rt2870 and rt3070 chipsets work best when controlled by Ralink's drivers. Only one of these modules should be loaded per network adapter.



To determine which modules control your USB WiFi adapter, insert it and run the following command in terminal

Code:

lsmod |grep rt

rt2870 devices are supported by Ralink's rt2870 driver (module rt2870sta) or by the rt2x00 project's driver (modules rt2800usb, rt2x00lib, rt2x00usb). rt3070 devices are supported by Ralink's rt3070 driver (module rt3070sta)



Blacklisting Modules:



To begin, unplug any Ralink USB WiFi adapters and restart your computer (or unload the modules).



To use rt2870sta and blacklist rt2800usb, run the following commands in terminal:

Code:

gksudo gedit /etc/modprobe.d/blacklist.conf

add these lines to the end of the file:

Code:

blacklist rt2x00usb

blacklist rt2x00lib

blacklist rt2800usb

Save the file, then insert your USB WiFi device.If this didn't work:



Your device either doesn't function with the driver you chose, or your WiFi Adapter's USB Device ID is not detected by that driver. If you're certain of which chipset is in your WiFi Adapter, you can modify and compile a kernel module that will detect and attempt to control any adapter with its USB Dev ID.



Determining Your Device's USB Device ID

You can check your USB Device ID using

Code:

lsusb

For example, lsusb states that a USB WiFi adapter has a device ID of 1234:7777

Code:

oo@oo:~$ lsusb

Bus 001 Device 004: ID 1234:7777 Brand

Compiling a New Kernel Module (Driver)

You'll need a compiler and Linux headers installed

Code:

sudo apt-get install build-essential linux-headers-generic



Modifying and Compiling RT2870STA:



Download a copy of Ralink's rt2870 USB driver from [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

Save it to your Ubuntu computer's desktop, then extract its contents using the following commands in terminal:

Code:

cd ~/Desktop

tar -xvf ~/Desktop/RT2870_LinuxSTA*.tgz

cd ~/Desktop/*2870*

Now you'll make some modifications, to add your device's USB Device ID. The following is an EXAMPLE. Using the lsusb command, it has been determined that an adapter has has the USB Device ID 1234:7777. MODIFY THESE INSTRUCTIONS TO USE YOUR USB DEV ID! You can put whatever you want for comments between */ s, they are meant to document the code.



Edit

Code:

s	gedit ~/Desktop/*2870*/common/rtusb_dev_id.c

add to the group:

Code:

{USB_DEVICE(0x1234,0x7777)}, /* Example WiFi Device Name */

Save.



You'll now configure the source to be compiled with support for NetworkManager and wext. NetworkManager is Ubuntu's default graphical method for configuring networking. It provides the icon in the "notification area" aka "system tray".



Edit

Code:

gedit ~/Desktop/*2870*/os/linux/config.mk

Change

Code:

# Support Wpa_Supplicant

HAS_WPA_SUPPLICANT=n

# Support Native WpaSupplicant for Network Maganger

HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n

to

Code:

# Support Wpa_Supplicant

HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Maganger

HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

Save.





In terminal:

Code:

cd ~/Desktop/*2870*

(If you're trying to compile a second time, please note: Run "make clean" before running "make" to remove your previous attempt.)

make

sudo make install

This installs the module rt2870sta.ko, but now you have 2 copies of it:

one in /lib/modules/`uname -r`/kernel/drivers/net/wireless and another at /lib/modules/`uname -r`/kernel/drivers/staging/rt2870. The one in the staging directory is the one that came with Ubuntu, which obviously doesn't work for you.



Before you delete your old driver, run the following commands to see if your newly compiled driver actually functions with your USB device.

Code:

sudo modprobe -r rt2870sta

sudo insmod /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2870sta.ko

sudo /etc/init.d/networking restart

sudo restart network-manager

If NetworkManager now works, congratulations.



Then delete the version of the rt2870sta module that came with Ubuntu (there might be better ways to do this, but it will allow the newly compiled one will load by default).

Code:

sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/staging/rt2870

Otherwise, you will have to run the above commands whenever you want to use the new driver. You will need to recompile this module every time a new Linux kernel is installed.

---

### Post by dafrasaga on 2010-08-19
Hi lajlev,
I have a new wifi adapter (belkin f6d4050) with rt3070 chip and I'll take that way, soon.. but I have a question:  why when I plug the adapter in the pc (laptop hp6930) and I type lsmod no rtxxxxx modules have been loaded??

cheers
gabriele

---

