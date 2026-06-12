---
title: "Bluetooth mouse issue"
date: 2005-08-21
forum: Hardware &amp; Laptops
---

### Post by iimre on 2005-08-21
Hi,
I'm new in this forum. I'm using Hoary 5.04 on an HP nc6000 notebook. My new toy is a Cellink BTM-5963 bluetooth mouse, which works fine except one issue. Whenever I restart the computer I have to pair (push the pairing button on the mouse) again. I can live with it , but it shoud remember for the device. The mouse is O.K., I have tried in XP and I had to paire only one time. Probably there is a solution for this. 
Please find below my related conf files.
I would appreciate any hint.
regards
Imre Ispanovits
-----------------------------------------  hcid.conf --------------------------------------------
#
# HCI daemon configuration file.
#
# $Id: hcid.conf,v 1.4 2004/04/29 20:14:21 holtmann Exp $
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
	security auto;
#	security none;
	
	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# PIN helper
	pin_helper /usr/bin/bluez-pin;

	# D-Bus PIN helper
	#dbus_pin_helper;
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class 0x100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	#
	#lm accept,master;
	#
	lm accept,master;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	#
	#lp hold,sniff;
	#
	lp rswitch,hold,sniff,park;

	# Authentication and Encryption
	auth disable;
	#encrypt enable;
}
----------------------------------------------- END -----------------------------------------
----------------------------------------- rfcomm.conf ------------------------------------
#
# RFCOMM configuration file.
#
# $Id: rfcomm.conf,v 1.1 2002/10/07 05:58:18 maxk Exp $
#

# example:
#
# rfcomm0 {
#  bind yes;
#	# Bluetooth address of the device
#	device 11:22:33:44:55:66;
#	# RFCOMM channel for the connection
#	channel	1;
#	# Description of the connection
#	comment "Example Bluetooth device";

rfcomm0 {
 bind yes;
# Bluetooth address of the device
    device 00:0A:94:C0:3C:7B;
	# RFCOMM channel for the connection
	channel	1;
	# Description of the connection
	comment "Cellink BTM-5963 mouse";
--------------------------------------- END --------------------------------------------

---

