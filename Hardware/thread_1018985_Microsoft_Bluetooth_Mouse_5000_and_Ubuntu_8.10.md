---
title: "Microsoft Bluetooth Mouse 5000 and Ubuntu 8.10"
date: 2008-12-22
forum: Hardware
---

### Post by markdr on 2008-12-22
Hi. I don't know whether this is specific to this mouse but I've been having lots of problems with it under Ubuntu 8.10. It works fine with Windows Vista. The bluetooth adapter I'm using is the Dell 370 Bluetooth Module.

When I first installed Ubuntu from the CD I was able to set up the mouse from the bluetooth icon on the panel and it worked great, but after a restart it wasn't working, but was still on the known devices list. If I ran the bluetooth device setup wizard again it would say the pairing failed, but after removing the mouse from the known devices list I could set it up as before which, again, lasted for that session only.

Well after downloading and installing all the updates released since the CD version of 8.10, it hasn't worked at all. The device setup wizard says "successfully configured new device" but the mouse doesn't work, and the flashing light on the mouse keeps flashing; it should stop once detected and working.

I've also tried some solutions on the net with terminal commands: I've added its MAC address to hcid.conf but when I do "sudo hidd --search" I get:

```
Searching ...
	Connecting to device 00:1D:D8:93:25:20
Can't get device information: Connection reset by peer
```

Any advice on where I'm going wrong? Thanks!

---

### Post by tankerkevo on 2008-12-22
There is a known issue with bluetooth being broken in Intrepid. This is recent within the last week.

Please post your issues on launchpad to help expedite attention to the issue:

[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/306721](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/306721)

---

### Post by HyRax on 2008-12-26
I've got the exact same mouse and have [worked around the problem](http://ubuntuforums.org/showpost.php?p=6438656&postcount=6). Still not perfect but at least you don't have to delete and re-pair the device each time - just power-cycle it and Intrepid picks it up a few seconds later.

---

### Post by Priit Tamboom on 2009-04-29
I just got the mouse working with restart/resume. I have followed [http://blog.chinthaka.org/2008/09/getting-microsoft-bluetooth-mouse.html](http://blog.chinthaka.org/2008/09/getting-microsoft-bluetooth-mouse.html)

However, additionally I had to change security from user to auto in order to reconnection at startup/resume works.

So change at /etc/bluetooth/hcid.conf

# Security Manager mode
# none - Security manager disabled
# auto - Use local PIN for incoming connections
# user - Always ask user for a PIN
#
security auto;

Instead of last step sudo hidd --seacrh, I cleaned all devices, reboot and added mouse again from applet.
After that everything works!

Anyhow you can follow bug about it [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/343727](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/343727)

---

