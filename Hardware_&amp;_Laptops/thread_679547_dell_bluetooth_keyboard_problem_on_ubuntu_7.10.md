---
title: "dell bluetooth keyboard problem on ubuntu 7.10"
date: 2008-01-27
forum: Hardware &amp; Laptops
---

### Post by Gilvin on 2008-01-27
First I have to sorry about my English, I'm Chinese so my English is really poor. 

dongle: HP USB BT Transceiver [1.2]

This dongle has legacy support that i can control the kbd in bios, here is the problem.

When my kbd started to idle, it cannot wake up anymore.

I tried a lot of configurations, like restart the /etc/init.d/bluetooth with crontab every 10 minutes; manually setup connection like hidd --connect aa:bb:cc:dd:ee:ff and any method I've found on the internet, but it still died after it idled, and I have to go back to Windows XP and press a button to make the kbd alive.

It came out a result: the dell bluetooth kbd and the dongle are reconized as ONE object in ubuntu 7.10, therefore when I search for kbd, the system only showed the MAC address of the dongle, not the kbd, and when the kbd idled, it can't wake up because without knowing the kbd's MAC address, the system didn't know what the keyboard is.

And I could not connect my cellphone to my computer, in the cellphone I could see both the kbd and the computer were on the device list, but Ubuntu still didn't make a move.

Can anyone tell me how to solve this problem.. it's killing me..

---

### Post by Gilvin on 2008-01-27
I think that my kbd is paired to my dongle, not the system, but don't know why when my kbd idles, it cannot wake up again, windows xp can, just press a button it comes alive.

this is my dongle's MAC, not the kbd's.
```
root@hyde-desktop:~# hcitool dev
Devices:
        hci0    00:10:C6:59:00:29
```

this is the result what hcitool scan brought out.
```
root@hyde-desktop:~# hcitool scan
Scanning ...
Inquiry failed: Connection timed out
```

this is my hcid.conf file:
```
#
# HCI daemon configuration file.
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

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
	passkey "1234";
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
```

this is my /etc/init.d/bluetooth config:
```
PATH=/sbin:/bin:/usr/sbin:/usr/bin
DESC="Bluetooth services"

HCID=/usr/sbin/hcid
HCIATTACH=/usr/sbin/hciattach
HCID_NAME=hcid
HCID_OPTIONS="-x -s"

#HID2HCI=/usr/sbin/hid2hci

UART_CONF=/etc/bluetooth/uart

RFCOMM=/usr/bin/rfcomm
RFCOMM_NAME=rfcomm
RFCOMM_CONF=/etc/bluetooth/rfcomm.conf

SDPTOOL=/usr/bin/sdptool

DUND_DAEMON=/usr/bin/dund
DUND_NAME=dund
PAND_DAEMON=/usr/bin/pand
PAND_NAME=pand
HIDD_DAEMON=/usr/bin/hidd
HIDD_NAME=hidd

DUND_ENABLED=0
PAND_ENABLED=0
HIDD_ENABLED=1
DUND_OPTIONS=""
PAND_OPTIONS=""
HIDD_OPTIONS="--master --server"
```

this is my /etc/defaults/bluetooth config:
```
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
HIDD_OPTIONS="--master --server"
# to make hidd always use a particular interface, use something
# like this, substituting the bdaddr of the interface:
# HIDD_OPTIONS="-i AA:BB:CC:DD:EE:FF --server"
#
# remove '--master' if you're having trouble working with Ericsson
# T630 phones with hidd operational at the same time.

############ COMPATIBILITY WITH OLD BLUEZ-PAN
# Compatibility: if old PAN config exists, use it
# rather than this file.
if test -f /etc/default/bluez-pan; then
    . /etc/default/bluez-pan
    return
fi
############
```

---

### Post by Gilvin on 2008-01-27
problem solved,  i bought another bluetooth usb dongle and it worked just like the manual said, really great.

it looks like some kind of unsolved bug on my old dongle...

---

