---
title: "Installing new Network Card (2nd one)"
date: 2008-02-09
forum: Hardware &amp; Laptops
---

### Post by InfoTech on 2008-02-09
I will be installing new (2nd one) NIC into my 7.10 Ubuntu Server. At this point, the server uses integrated NIC for network connection, but I want to use it as firewall as well, so I need 2 NICs

Since I have no experience in adding new hardware in Linux (especially in CLI), I need some help on how to proceed after I plug the NIC into a PCI slot (some cheap D-Link 10/100 model) and turn the power on.

Thanks a lot.
Regards

---

### Post by RudolfMDLT on 2008-02-09
Once you have switched the power on, and have logged in, issue the following command: 

> lspci

Search the list and see whether you see both network cards

and then

> ifconfig

You should now see eth0 and eth1 ?

You shouldn't have to install drivers.

> ifconfig - lists IP address (similar to ipconfig in Windows)
iwlist scan - shows wireless networks that are available in the area along with basic encryption information
lshw -C network - Shows interface and driver associated with each networking device
lspci -nn - Shows hardware connected to the pci bus
lsusb - Shows USB connected hardware
lshw -C usb - Additional info on USB related hardware (good for USB dongles)
cat /etc/modprobe.d/blacklist - List modules that will not be loaded by the Operating System at boot time
lsmod - lists currently loaded kernel modules. (Example usage - lsmod | grep ndiswrapper)
route -n - Lists kernel IP routing table -- Good for troubleshooting problems with the gateway (netstat -rn = equivalent command)
sudo route add default gw 192.168.1.1 - Example of how to set the default gateway to 192.168.1.1
sudo route del default gw 192.168.1.1 - Example of how to delete the default gateway setting
sudo modprobe ***** - Loads the kernel module **** . (Example usage - sudo modprobe ndiswrapper, sudo modprobe r818x, sudo modprobe ath_pci)
sudo modprobe -r **** - Unloades the kernel module ****. (Example usage - sudo modprobe -r ndiswrapper)
sudo ifup/ifdown <interface> - Brings up/down the interface and clears the routing table for the specified interface
sudo ifconfig <interface> up/down - Brings up/down the interface for the specified interface
sudo dhclient <interface> - Request IP address from DNS server for specified interface
sudo dhclient -r <interface> - Release IP address associated with specified interface
sudo iptables -L - Lists firewall rules
dmesg | more - Lists boot log -- good for troubleshooting problems with modules/drivers not being loaded
uname -r - Displays kernel version
/etc/iftab (Feisty and pre-releases (Edgy, etc)) - /etc/udev/rules.d/70-persistent-net.rules (Gutsy) - File which assigns logical names (eth0, wlan0, etc) to MAC addresses
cat /etc/resolv.conf - Lists DNS servers associated with network connections (Network Manager)
/etc/dhcp3/dhclient.conf - File which sets or modifies dns (domain name servers) settings



This should atleast get you started using doing networking in the BASH.

---

### Post by InfoTech on 2008-02-09
Thanks a lot. I will do this first thing in the morning.... (some 9 hours more). The OS will "remember" new NIC after the reboot?

---

### Post by RudolfMDLT on 2008-02-09
The OS doesn't remember anything. it just installs it as it goes, every boot as far as I know.

You have a config file here:

> /etc/network/interfaces

open up the terminal and do

> cat /etc/network/interfaces

Your network card can fail or blow up and you can replace it with a new one and Ubuntu should just apply the old settings to the new card.

also, here is my config:

> auto eth0
iface eth0 inet static
         address 192.168.10.6
         netmask 255.255.255.0
         broadcast 192.168.10.255


[COLOR="Red"]auto eth0:1[/COLOR]
iface eth0:1 inet static
address 10.0.0.19
netmask 255.255.255.0
#gateway 10.0.0.1


The red card is an alias. In Ubuntu you can have multiple IP ranges and address on 1 card - It's like having multiple network cards! :)

---

### Post by InfoTech on 2008-02-09
Ah, so, as the OS boots up, it detects the cards that are listed in /etc/network/interfaces, recognizes them and apply the appropriate driver? 

Did I understood this right?

---

### Post by RudolfMDLT on 2008-02-10
As the OS boots up, it detects everything on the system. Do the command "lspci". When it finds a network card, the card gets a name, eth0. eth0 then gets given settings by the system which are in the interfaces file.

So, did it work as easy!? :)

---

