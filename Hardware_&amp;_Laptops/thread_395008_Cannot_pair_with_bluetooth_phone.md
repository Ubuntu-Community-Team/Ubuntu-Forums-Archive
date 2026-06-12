---
title: "Cannot pair with bluetooth phone"
date: 2007-03-27
forum: Hardware &amp; Laptops
---

### Post by kirenpillay on 2007-03-27
Hi

I cannot pair with my bluetooth phone. I'm runned Ubuntu 6.10. when i peform an "hcitool cc 
"and then "hcitool auth " as in the How-to, I get an error.

The syslog complains about a passkey agent not being registered.

I have seen other posts but it looks like a mix of totally different solutions which is confusing to me. I am on the latest blue-utils packages, the ones that come with6.10 (3.7.1). I notice certain posts are mentioning kdebluetooth but I'd like to keep my system using gnome as far as possible.

Please help!

Regards
Kiren

---

### Post by kirenpillay on 2007-04-12
Still can't connect. I no there are posts with suggestions, but these are no help. 

1. Should I compile the passkey-agent and install it? I don't seem to have all the dbus packages.
2. I've tried the hidd --connect , that didn't work.
3. I've tred the dbus --send command and it doesn't work. I've tried to pair from my phone and the logs just show the link request failed.
4. I've tried the bluez-pin pin_helper helper, restarted the bluetooth stack, and still get the 'passkey_agent' not registered message (that doesn't make sense)

I notice another thing. I stopped the bluetooth stack, and am still able to do an hcitool cc, which connects to the phone. I just can't auth. 

Please help.

---

