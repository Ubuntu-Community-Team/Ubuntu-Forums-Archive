---
title: "pptpconfig error and VPN"
date: 2005-11-13
forum: General Help
---

### Post by neur0 on 2005-11-13
When I try to run pptpconfig to use GUI to configure my VPN connection, I get this error:

Warning: dl(): Unable to load dynamic library '/usr/lib/php-pcntl/lib/php/extensions/no-debug-non-zts-20020429/php_gtk.so' - libglade.so.0: cannot open shared object file: No such file or directory in /usr/bin/pptpconfig.php on line 31

Fatal error: Cannot instantiate non-existent class:  gdkcolor in /usr/bin/pptpconfig.php on line 96

I do have php-pcntl 4.4.1-2 instaled btw.

Or if anyone has any other suggestion on how to configure my vpn connection, please tell me. I've been trying to connect to the net for 3 days, and I simply don't know what else to try.

---

### Post by hajk on 2005-11-14
What exactly is your problem ...does your DSL connection (using PPTP) not work? ...or are you trying to get VPN working on an existing (and working) DSL connection to the internet? If the latter, what kind of VPN client are you looking for... IPSec based? Are you running a firewall, like Firestarter?

---

### Post by neur0 on 2005-11-14
No, it is not a DSL connection at all. The way my ISP works is somethink like this:
I have a wireless connection, and this connects me to my ISP's VPN and so I get connected to the internet. In windows xp, this is done not so different then setting up a dial-up connection:
*Create a new connection > Connect to the network at my workplace > Virtual Private Network connection > ...*
How do I set it up in Ubuntu?

---

### Post by hajk on 2005-11-14
Well, in that case you don't need PPTP as far as I know. VPN works with a "tunnel" through the regular internet connection, in your case a wireless link to an access point. So that is what you should get working first.

After that, you should inquire what kind of VPN client is needed; this is often a "Cisco" client, which is IPSec-based. In that case you can install the Ubuntu "vpnc" package to get you up and running.

---

### Post by neur0 on 2005-11-14
Great, but how do I create this tunnel? (did I mention I am a Linux newb?)
And how do I get the "vpnc package?" Its not in the Synaptic list.

---

### Post by hajk on 2005-11-15
Whoa, not so fast! First ask at your school whether the Cisco VPN client will work, and -- if so -- the following information: 
1. address of the gateway (likely the wireless access point)
2. the ipsec group ID
3. the ipsec group secret
in addition to your own ID and password.

The "vpnc" package is in the universe repository, so edit your /etc/apt/sources.list ("sudo gedit") to enable this. The "vpnc" package is a replacement for the Cisco VPN client, so you should only install it if your school uses this IPSec-based method for VPN.

---

