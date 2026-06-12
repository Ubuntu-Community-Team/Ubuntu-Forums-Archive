---
title: "Bluetooth stuck in &quot;Connectible Mode&quot;"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by ctsdownloads on 2007-04-25
I have spent the better part of an hour wondering what the hell is keeping my supported dongle in connectible mode when it should clearly be in discoverable mode.

First, I uninstalled and reinstalled bluetooth-utilz and gnome-bluetooth, then restarted services. Still connectible, not discoverable.

Examined my hcid.conf until the world looked level.

---
> 
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
	class 0x3e0100;

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


And I am simply not understanding what I missed?? Tried other users as well, they too are stuck in this damned connectible mode, thus ensuring that I will never be able to connect to my desktop with bluetooth. what did I miss? ](*,)

---

