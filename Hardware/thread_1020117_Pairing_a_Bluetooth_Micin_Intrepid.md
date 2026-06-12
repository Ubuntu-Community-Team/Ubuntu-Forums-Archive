---
title: "Pairing a Bluetooth Micin Intrepid"
date: 2008-12-23
forum: Hardware
---

### Post by tankerkevo on 2008-12-23
I can not get my Sony PS3 Bluetooth microphone paired with my laptop running Intrepid 8.10. The gnome applet can see the device, but when it tries to connect it never asks me for a pin code/pairing key, which for this device is 0000. I have gotten my BT keyboard working (for the moment anyways), so I know it's not the Bluetooth adapter dongle.

I have also tried the script found here: [http://www.technetra.com/2008/11/22/pairing-stubborn-bluetooth-devices-in-fedora-10-ubuntu-ibex/](http://www.technetra.com/2008/11/22/pairing-stubborn-bluetooth-devices-in-fedora-10-ubuntu-ibex/)

But again, even using that script I never get prompted to enter a pin code. I tried that script with and with-out the commented optional lines at the bottom it.

On a side note, I have also tried pairing a Mad Catz Bluetooth microphone with the exact same results.

Does anyone have a process for this laid out they can share or any suggestions?

If you need more information let me know. Thanks!!! 


Inventory of issue:

Sony PS3 Bluetooth Headset
USB Bluetooth Dongle (Generic)
Dell 1525 Laptop
Ubuntu Intrepid Ibex 8.10

Relevant Packages Installed:
  blueman0.5-0ubuntu1     
  bluetooth       4.12-0ubuntu5
  gnome-bluetooth 0.11.0-0ubuntu3
  libbluetooth2   3.29-0ubuntu1
  libbluetooth3   4.23-0ubuntu2~git20081206
  python-bluez    0.15-1build1
  bluez           4.12-0ubuntu5
  bluez-alsa      4.12-0ubuntu5
  bluez-audio     3.26-0ubuntu8
  bluez-btsco     1:0.50-0ubuntu3
  bluez-compat    4.12-0ubuntu5
  bluez-cups      4.12-0ubuntu5
  bluez-gnome     1.8-0ubuntu1
  bluez-gstreamer 4.12-0ubuntu5
  bluez-utils     4.12-0ubuntu5  
  python-bluez    0.15-1build1

Contents of /etc/default/bluetooth
> # Defaults for bluez

# start bluetooth on boot?
# compatibility note: If this variable is not found bluetooth will
# start
BLUETOOTH_ENABLED=1

# This setting will switch HID devices (e.g mouse/keyboad) to HCI mode, that is
# you will have bluetooth functionality from your dongle instead of only HID.
# Note that not every bluetooth dongle is capable of switching back to HID
# mode, see [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=355497](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=355497)
HID2HCI_ENABLED=0
HID2HCI_UNDO=0
HIDD_ENABLED=1



Contents of /etc/bluetooth/hcid.conf (Note I have also tried the "security" value set as "auto" already.

> #
# HCI daemon configuration file.
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit no;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security user;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# Default PIN code for incoming connections
	passkey "0000";
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class 0x000100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;
	discovto 0;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;
}


Thanks again!

---

