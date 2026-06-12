---
title: "Renesas USB 3 does not mount external drive"
date: 2018-06-20
forum: Hardware
---

### Post by gdesilva on 2018-06-20
Hi, I am using Ubuntu 18.04 and having some issues auto mounting external HDDs.

I have a Renesas uPD720201 USB 3.0 card and also built in USB 2.0 on my system.

If I plug an external HDD into any of the built in USB2.0 ports the system automatically mounts them. However, if I plug the same drive into the Renesas card the system fails to recognize it. No problems with USB flash drives which get recognized in both situations.

I did restart udev but no luck - however, on a couple occasions I have been able to access the HDD when plugged into the Renesas card but cannot work out what the specific conditions were - rebooting does not replicate the condition.

Any suggestions will be greatly appreciated.

Thanks.

---

### Post by rbmorse on 2018-06-24
Is the external hard drive powered through the USB port, or does it have its own power supply?  

If the drive gets power through the port, it's possible that the Renesas card isn't delivering sufficient power to the external hard drive.  

I have two WD passport Ultras (1TB) that don't consistently work with certain USB 3 ports on my machine.  Other ports work fine, as do all the USB 2 ports, and they also work consistently from the USB 3 hub built into my display and an external hub that has its own power supply.   WD support suggested the power issue and all the testing I've done since seems to support that hypothesis. 

My 2Tb external Seagate, on the other hand, works fine on any ports.

---

### Post by gdesilva on 2018-06-27
@rbmorse, thanks for the response and what I have observed is consistent with what you have mentioned above - ie the Renesas card not delivering sufficient power.

My HDD is connected via a powered hub and it works without any issues on all other USB2 ports.

Interestingly, if I follow the following steps in the strict order, I can get it to work. The order is;

1. unplug the USB hub from the Renesas port
2. turn off power to the USB hub.
3. plug the HDD to a port in the hub
4. power on the hub
5. plug the hub to a Renesas port

If I do not follow the above step in the strict order then the HDD is not recognized!

I guess I just have to live with it.

---

