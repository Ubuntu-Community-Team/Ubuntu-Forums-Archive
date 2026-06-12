---
title: "Acer Aspire One +  Wireless Not Working"
date: 2008-09-09
forum: Hardware
---

### Post by somesnapper on 2008-09-09
Hello all

I followed the [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) and still cant get WIfi working properly. I've done it twice!

If I right click on the nm-applet, I do not have an option to "enable wireless" only "enable network".

I'f i open up system>administration>network - i'm able to detect wireless networks. After entering the information properly - I cant successfully connect to any websites. 

If I do a iwconfig I get:

wifi0: no wireless extensions

If I set it to roaming mode - it never detects any wireless networks.

Under Network Tools - I have "Ethernet interface (eth0), Unknown interface (wifi0), Unknown interface (ath0), Unknown interface ath0:avahi:)



Cant browse the net - cant ping anything

Please help.

---

### Post by somesnapper on 2008-09-10
Under Devices - Network tools - if I chose any network device and pick "Configure" i get an error message saying the device isnt found.

Now my Eth0 connection doesnt work either. Its not updating its IP address from the DHCP server.

Does anyone know how to reinstall the Eth0 and wireless drivers?

Should the wireless adapter be "ath0" or "wifi0" ? 


Thanks

---

### Post by somesnapper on 2008-09-10
I just checked my hosts and resolv. files and they seem fine.

What a bummer :(

---

### Post by somesnapper on 2008-09-10
During the Acer One Ubuntu installation document above - they ask to disable all items in 
System - Administration - Hardware Drivers
must these two remain disabled?

---

### Post by somesnapper on 2008-09-10
Under system tools > network tools I see  the following devices

Ethernet Interface (eth0)
Unknown interface (Wifi0)
Unknown interface (ath0)
Ethernet interface (eth0:avahi)

Can someone please tell me if this looks ok? 

Ive been searching for hours - no luck.

---

### Post by somesnapper on 2008-09-10
This forum moves fast :) thoughts?

---

### Post by somesnapper on 2008-09-10
Nothing at all?

---

### Post by Aearenda on 2008-09-10
I suspect perhaps part of the problem is that you replied to your own post very quickly, so those who respond to unanswered posts probably never saw yours. Bear in mind time zone differences around the world - my day is probably your night.

I have only just got an Aspire One, and probably won't be trying to install Ubuntu on it for a few days or weeks yet. When I do, if I hit the same problem, I'll let you know what happens.

In the meantime, please make sure you have followed the guide carefully, and make sure that /etc/network/interfaces has no entries in it for eth0, ath0 or wifi0. 

If you have applied any kernel updates, make sure you rebuild the drivers as described in the Wireless section of the guide. I think the drivers should remain disabled in 'hardware drivers' as described. Adding the ath_pci entry to /etc/modules forces the correct module to load.

If you have done all this and it still does not work, please take a look at the output of ```
dmesg
``` and see if it offers any clues about the wireless adapter. You can post any likely-looking error messages here, but please don't just post the whole thing!

---

### Post by somesnapper on 2008-09-10
Thank you. Typing sudo modprobe ath_pci did the trick. 

Wireless working fine.

Ethernet isnt. But ill work that out soon

---

### Post by Aearenda on 2008-09-10
Ok, good - for the wired connection, make sure nothing for it is in /etc/network/interfaces - or at the most this:
```

auto eth0
iface eth0 inet dhcp

```

It is supposed to 'just work', so make sure you haven't blacklisted its driver too!

Then look through the dmesg output to see if there is anything relevant.

---

### Post by Aearenda on 2008-09-11
Well, I couldn't resist in the end - my Aspire One now has Ubuntu on it, with the Netbook Remix additions. It looks great! I followed the guide, the wired interface 'just worked' and the wireless interface worked once the new module was compiled, including after a reboot. Good luck with sorting your wired interface out!

---

