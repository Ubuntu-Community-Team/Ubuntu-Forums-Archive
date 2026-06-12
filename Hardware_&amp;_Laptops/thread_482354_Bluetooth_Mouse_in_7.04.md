---
title: "Bluetooth Mouse in 7.04"
date: 2007-06-23
forum: Hardware &amp; Laptops
---

### Post by fogNL on 2007-06-23
I have a Logitech Bluetooth mouse and I'm trying to hook it up with my HP-Compaq NC6400 laptop via bluetooth.

In order for it to work, I have to go into the console and run hcitool scan in order to get the address of the mouse and then run hidd --connect to connect to the mouse.  The problem is, I have to do this on every reboot, or even if I leave my laptop for a couple of hours and come back to it.

I'm running Kubuntu and therefore KDE.  The strange thing is, after it "timeouts" when left idle, when I move the mouse, the KDEbluetooth icon in the system tray appears and disappears each time i move the mouse.  It's not until i go into the console and re-type the hidd --connect command does the icon actually stay.

I've read around a bit, and found out how to manually add my mouse to my /etc/bluetooth/rfcomm.conf file to automatically connect to the mouse on startup, but it doesn't work.

It seems to me like it should be easier to connect the mouse to my system and not have to worry about the console all the time to use it.

Any suggestions?

---

### Post by quantumchicken on 2007-06-28
I have the same problem.  I have a Microsoft bluetooth mouse that i used to use with windows.  Once i have clicked the reset button on the underside of the mouse, all i have to do to connect is type:

 sudo hidd --search

and it connects with no problems.  However i cannot get this to happen after i have rebooted.  Even after modifying the bluetooth file so that it reads:

# Defaults for bluez-utils

# This file supersedes /etc/default/bluez-pan.  If
# that exists on your system, you should use this
# file instead and remove the old one.  Until you
# do so, the contents of this file will be ignored.

# start bluetooth on boot?
# compatibility note: If this variable is not found bluetooth will
# start
BLUETOOTH_ENABLED=1

############ HIDD
#
# To have Bluetooth mouse and keyboard support, get the
# Linux 2.6.6 patch or better from bluez.org, and set 
# HIDD_ENABLED to 1.
HIDD_ENABLED=1
HIDD_OPTIONS="-i 00:50:F2:E6:21:98 --master --server"
# to make hidd always use a particular interface, use something
# like this, substituting the bdaddr of the interface:
# HIDD_OPTIONS="-i AA:BB:CC:DD:EE:FF --server"

where the file obviously continues on.  I have no idea what to do now.  Can anybody help?

---

