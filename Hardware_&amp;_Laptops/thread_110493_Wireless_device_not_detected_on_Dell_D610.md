---
title: "Wireless device not detected on Dell D610"
date: 2005-12-30
forum: Hardware &amp; Laptops
---

### Post by cnkbrown on 2005-12-30
I have a dell D610 with updated Breezy, and after fiddling for hours with the damn thing, I am convinced that the Intel PRO/Wireless device is not being detected.  I don't see anything about it listed in `lspci` or 'lshw` outputs, and dmesg shows the driver loads, but there is no message indicating the hardware was found.  ifconfig shows no "eth1" interface, and ifup --force eth1 shows "no such device".  iwconfig shows all other interfaces as "no wireless extensions".

I checked the BIOS, and the wireless is configured for "Fn+F2/App" and is set to "On".  I added 'ipw2200' to /etc/modules, I downloaded and installed the ipw2200-fw-2.3 in /usr/lib/hotplug/firmware, I created a file /etc/modprobe.d/ipw2200 that contains "options ipw2200 hwcrypto=0".  Also, added "auto eth1" to /etc/network/interfaces.

Wireless works fine under Win XP, so I don't think the actual hardware is faulty.

Any tips for what to look at on this?  Thanks,

---

### Post by byen on 2005-12-31
can you tell us the make of your wireless card? you have mentioned Intel Pro wireless...as far as I can tell I think that card is made my broadcom and if that is the case you might wanna look into this thread

[http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)

Hope it helps. Good luck.

---

### Post by kingsidy on 2005-12-31
the intel pro 2200 should be supported by default. Mine worked out of the box (intel pro 2200 b/g). Do you the interface when you go into system networking, it is usually listed there. i think i checked the activate checkmark and i was good to go

---

### Post by jackdirt on 2005-12-31
I don't know much about linux but to enable my wireless I had to go to system/administration/networking and turn it on via properties I don't know if it helps but it worked for me when i couldnt find it

---

### Post by vasudevank on 2005-12-31
intel pro wireless is completely supported by linux, u may want to try to gentoo portage drivers to see if that works

---

### Post by cnkbrown on 2006-01-02
I've read the card is probably a 2915, which is 2200 compatible.  I was thinking of trying the ndiswrapper, but I've seen so many posts that say, "the 2200 just works", that I wanted to make sure I hadn't missed something obvious, first.

---

### Post by cnkbrown on 2006-01-02
One other item.   There is an 'eth1' interface in /etc/network/interfaces, but it cannot be brought up, and it does NOT appear in any of the system admnistration applets.  I did consider that the card might be trying to use some other interface name, but the 2200 driver outputs some of its parameters in /sys/.../ipw2200, and the iface parameter shows '<NULL>'.

---

### Post by Luna.jp on 2007-11-08
Did you fix this problem?

---

