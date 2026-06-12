---
title: "Is it safe to ignore this?"
date: 2007-08-25
forum: Hardware &amp; Laptops
---

### Post by Secession on 2007-08-25
Upon returning from standby, I sometimes get error messages from my Bluetooth about not being able to find a server which don't seem to affect anything.  Today I got this message on my Sony VAIO.

> To use the kbtobexsrv service, some other devices might require a modified class number for your bluetooth adapter in /etc/bluetooth/hcid.conf. 
Currently the class is set to 0x0. We suggest you change this to something like 0x100000 instead and restart BlueZ's hcid. The service will be activated anyway.

I had a look at the file and it isn't 0x0 at all.

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
```

I carried on regardless and everything seems OK.  I only ask because I've learned through various unpleasant episodes not to ignore error messages even if they seem irrelevant.  Sometimes you can though if you can be really sure what's going on.  What do you think?

Thanks in advance for your help.

---

