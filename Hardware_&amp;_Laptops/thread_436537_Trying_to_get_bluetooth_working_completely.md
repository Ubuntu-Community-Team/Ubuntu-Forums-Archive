---
title: "Trying to get bluetooth working completely"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by Funzo22 on 2007-05-07
Ok, I just got a new sony Ericsson phone, and I installed anyremote on both my computer and the phone already, and I have gotten the computer and the phone to link via bluetooth, now I am getting a stranger error message that I cant get rid of.

Here are some things that I think are useful:

First of all, my /etc/bluetooth/rfcomm.conf is all commented out.


> dustin@dneray-desktop:~$ sudo cu -l /dev/hci0 -s 19200
cu: open (/dev/hci0): No such file or directory
cu: /dev/hci0: Line in use
dustin@dneray-desktop:~$ 



> dustin@dneray-desktop:~$ anyremote -f '/home/dustin/Desktop/anyremote-2.11/cfg-examples/AT-mode/mouse.cfg' 
CFG: Use cfg file >/home/dustin/Desktop/anyremote-2.11/cfg-examples/AT-mode/mouse.cfg<
INFO: log file is /tmp/anyremote.log.dustin
ERROR: can't open /dev/rfcomm0
ERROR: open port
INFO: Already closed ?
ERROR: close port
dustin@dneray-desktop:~$ 


Relevant stuff from the log:
> [Mon May  7 23:20:25 2007] - DEBUG - mainRoutine
[Mon May  7 23:20:25 2007] - INFO - openPort()
[Mon May  7 23:20:25 2007] - DEBUG - Serial Client mode. Use device /dev/rfcomm0
[Mon May  7 23:20:25 2007] - ERROR - can't open /dev/rfcomm0
[Mon May  7 23:20:25 2007] - INFO - Stop process ...

My /etc/bluetooth/hcid.conf (untouched)
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




I'm not sure what else to post, but if you need anything else, just ask.

Thanks in advance



Dustin

---

### Post by Funzo22 on 2007-05-07
Edit: I solved my own problem, all I had to do was pair the devices with the rfcomm command, instead I was just doing it through the phone before

---

