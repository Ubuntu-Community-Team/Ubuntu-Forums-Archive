---
title: "Wireless network suddenly not working"
date: 2008-04-22
forum: Hardware
---

### Post by agger on 2008-04-22
I have a MSI S271 laptop with Ubuntu Gutsy installed. All of a sudden (i.e., the last few days) it refuses to connect to our wireless network.

The laptop is equipped with a  RaLink RT2500 802.11g wireless card which has hitherto worked fine.

It is activated and sees the home network, as shown by the output from the connection attempt in syslog (sarasvati is the laptop's host name):

```

Apr 22 21:22:43 sarasvati NetworkManager: <debug> [1208892163.976860] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'Agger' 
Apr 22 21:22:43 sarasvati NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / Agger 
Apr 22 21:22:43 sarasvati NetworkManager: <info>  Deactivating device wlan0. 
Apr 22 21:22:43 sarasvati dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Apr 22 21:22:44 sarasvati NetworkManager: <info>  Device wlan0 activation scheduled... 
Apr 22 21:22:44 sarasvati NetworkManager: <info>  Activation (wlan0) started... 
Apr 22 21:22:44 sarasvati NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 22 21:22:44 sarasvati NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Apr 22 21:22:44 sarasvati NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Apr 22 21:22:44 sarasvati NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Apr 22 21:22:44 sarasvati NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Apr 22 21:22:44 sarasvati NetworkManager: <info>  Activation (wlan0/wireless): access point 'Agger' is unencrypted, no key needed. 
Apr 22 21:22:45 sarasvati NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Apr 22 21:22:45 sarasvati NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Apr 22 21:22:45 sarasvati NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant4^I' 
Apr 22 21:22:45 sarasvati NetworkManager: <info>  SUP: response was 'OK' 
Apr 22 21:22:45 sarasvati NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Apr 22 21:22:45 sarasvati NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Apr 22 21:22:45 sarasvati NetworkManager: <info>  SUP: response was 'OK' 
Apr 22 21:22:45 sarasvati NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Apr 22 21:22:45 sarasvati NetworkManager: <info>  SUP: response was '0' 
Apr 22 21:22:45 sarasvati NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 4167676572' 
Apr 22 21:22:45 sarasvati NetworkManager: <info>  SUP: response was 'OK' 
Apr 22 21:22:45 sarasvati NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Apr 22 21:22:45 sarasvati NetworkManager: <info>  SUP: response was 'OK' 
Apr 22 21:22:45 sarasvati NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Apr 22 21:22:45 sarasvati NetworkManager: <info>  SUP: response was 'OK' 
Apr 22 21:22:45 sarasvati NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Apr 22 21:22:51 sarasvati NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Apr 22 21:23:26 sarasvati last message repeated 6 times
Apr 22 21:23:43 sarasvati last message repeated 3 times
Apr 22 21:23:45 sarasvati NetworkManager: <info>  Activation (wlan0/wireless): association took too long (>60s), failing activation. 
Apr 22 21:23:45 sarasvati NetworkManager: <info>  Activation (wlan0) failure scheduled... 
Apr 22 21:23:45 sarasvati NetworkManager: <info>  Activation (wlan0) failed for access point (Agger) 
Apr 22 21:23:45 sarasvati NetworkManager: <info>  Activation (wlan0) failed. 
Apr 22 21:23:45 sarasvati NetworkManager: <info>  Deactivating device wlan0. 

```

Any clues to what might go wrong? Other computers in the house connect to the network without problems, and this one connects to the wireless router without problems using an Ethernet cable and one of the router's Ethernet ports (this is what I'm doing right now).

I'd be grateful for any pointers or clues.

br
Carsten

---

### Post by agger on 2008-04-23
The "hardware properties" application seems to indicate that the system is using a fairly generic driver from freedesktop.org - however, this shouldn't be a problem since it has been set up like that a long long time.

Could a recent update have "disturbed" the driver for the RaLink RT2500 wifi cards? Would upgrading to Hardy solve the problem?

---

### Post by MacGeneral on 2008-05-22
might be a broken driver in the 2.6.24.x kernel!?

I experienced such problems when using a 2.6.24 kernel which includes the RaLink drivers for the first time.

```
lsmod | grep rt
```
=> If you see any rt61, rt73 or rt2x00 ending with pci or usb, then its the driver integrated into the kernel (the one from the website doesn't have pci or usb at the end)

So you could either compile a Vanilla Kernel yourself, wait until the Ubuntu Kernel gets updated or compile the Driver from [rt2x00.serialmonkey.com]("http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads") [(direct link)]("http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz") which would be the easiest way to do that! (simple make and sudo make install and you are done!)


As you can see on that website the driver in 2.6.24 is "somewhat buggy"

> rt2x00 enters mainline kernel - January 2008

Hi All,

two days ago, January 24th, Linux Kernel 2.6.24 was released. This is the first mainline kernel that includes (sadly a somewhat buggy) rt2x00 release.

Our rt2x00 driver has reached a broader audience, and we all wish to congratulate the developers and most importantly all of our users who provided numerous bug reports and even fixes.

Now, lets continue to work towards a stabler driver!

Luis Correia
rt2x00 Project Administrator


To compile it do the following:
```
$ tar -xzzf rt2500-cvs-daily.tar.gz
$ cd rt2500-cvs-2008052218 (repace it to fit your folder name)
$ make
$ sudo make install
```


Try the following after you installed it
```
$ sudo rmmod rt2500pci
$ sudo rmmod rt2x00pci
$ sudo rmmod rt2x00lib
```

or for an USB device

```
$ sudo rmmod rt2500usb
$ sudo rmmod rt2x00usb
$ sudo rmmod rt2x00lib

```

and then
```
$ sudo modprobe rt2500
```


If rmmod doesn't exist use "modprobe -r" or something similar ;) (Im writing that on Fedora which doesn't have the rmmod command, but Debian has it and Im pretty sure Ubuntu does as well)


if it works now, then blacklist the Kernel integrated driver (until a new Kernel gets out - it works for me with the 2.6.25 Kernel releases!)
```
$ sudo nano /etc/modprobe.d/blacklist
``` (you can use gedit as well if you feel more comfortable with it!)

and add the following at the end of the file:
```
# RaLink drivers integrated into the kernel
blacklist rt2500pci
blacklist rt2x00pci
blacklist rt2x00lib
```

save it and you are done. If you restart now the Kernel will always take the driver you compiled yourself and not the buggy one!


Note: other users might want to do the same with the following drivers (all):
rt2400pci  rt2500usb  rt2x00pci  rt61pci
rt2500pci  rt2x00lib  rt2x00usb  rt73usb
remember to remove first the specific driver, then the rt2x00pci or rt2x00usb and rt2x00lib as last one!

---

