---
title: "Naming Interfaces"
date: 2008-10-09
forum: General Help
---

### Post by SteelWo1f on 2008-10-09
Is there a way to give a network interface a name such as external so that I can run a command like 'tcpdump -i external'?

If possible I want to be able to do it based on the device name, ie so that /dev/eth1 is always connect. I dont want to do it based on MAC addresses, but if that is the only way then I guess thats ok.

---

### Post by caleb12 on 2008-10-09
UDEV names all your devices and if I recall correctly those vaules can be adjusted in this file:

/etc/udev/rules.d/ 

ls the contents, there will be a bunch of files... you will be looking for two in particular... for instance mine are called:

70-persistent-net.rules
75-persistent-net-generator.rules

Edit the first file, persistent-net.rules - in it you will have a couple lines looking something like this:

# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:c0:9f:71:37:ba", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


Change NAME="my_device_name_goes_here" 

I always change my wlan0 to eth0, since I use it most often...

---

### Post by SteelWo1f on 2008-10-09
Thanks. That worked just as I want it too. I made up this little script to do all the dirty work for me.

#!/bin/sh
# Renames a network interface

if [ ! -n "$2" ]
then
    echo "Usage: `basename $0` [ old name ] [ new name ]";
    exit 1;
fi

cat /etc/udev/rules.d/70-persistent-net.rules | sed "s/$1/$2/" > /tmp/net.rules && mv /tmp/net.rules /etc/udev/rules.d/70-persistent-net.rules
cat /etc/network/interfaces | sed "s/$1/$2/" > /tmp/interfaces && m
v /tmp/interfaces /etc/network/interfacse

---

