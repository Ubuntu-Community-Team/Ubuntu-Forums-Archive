---
title: "Mighty Mouse Buttons don't work"
date: 2009-01-12
forum: Hardware
---

### Post by licensedorchid on 2009-01-12
Hi! I have been using a mighty mouse with Ubuntu since the 7 series came out. (I think I started with 7.10). It has worked flawlessly, but last night I pulled out the old l2000 laptop, and threw in an 8.10 disc. Install went fine, and I love how easy it was to get me broadcom wireless working. (That's kinda a first!)
Anyway, here is the problem. I can get my mighty mouse to pair and connect. The scroll wheel works, and the mouse moves the cursor, but none of the buttons seem to work. I have done some searches of the forums, and hit up the google (haha), but none of the fixes I have found have made a difference. I was wondering if anyone had an idea of where I should look.
The mighty mouse used to work fully if I threw a "sudo hidd --connect" at it, but now, not so much. 
Thanks!

---

### Post by licensedorchid on 2009-01-12
Well, firstly, bump. Secondly, this is the contents of my hcid.conf. Don't know if I need it or not.```

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
	security auto;

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
	lm none;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;


device 00:1E:52:CF:68:61 {
    name "Mighty Mouse"
    auth enable;
    encrypt enable;
}

```

---

### Post by licensedorchid on 2009-01-16
This worked with 7.10. If someone could at least point out to me what has changed with the bluetooth stack since then, that would be helpful. (I know *something* changed, I just don't know what!)

---

### Post by ZAxisMapping on 2009-02-15
I'm not certain the cause right now, but I can verify that I have experienced identical behavior (scroll wheel works fine, all other buttons are unresponsive).

Worked in Ubuntu 7.10.

(On the plus side, the keypad on my apple aluminum keyboard now works)

---

### Post by kevintyk on 2009-03-07
Same problem here, anyone know how to fix this? I'm using ubuntu 8.10 64 bits

---

### Post by andreyvasilyev on 2009-03-27
I have the same problem. Does anybody have found any solutions?

---

