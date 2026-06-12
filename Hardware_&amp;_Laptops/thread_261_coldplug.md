---
title: "coldplug?"
date: 2004-10-12
forum: Hardware &amp; Laptops
---

### Post by Anonymous on 2004-10-12
Hi! How about coldplug support?
I have a usb pendrive and a usb hd, since the pendrive is easy to unplug - plug in order to let hotplug manage the mounting, the hd, instead, is "meant" to be demi-unremovable, is plugged on the back of the case, difficult to reach, and I would like to see it mounted everytime... I've already made an init script to mount all /dev/sd ??* devices, but with the power of hotplug this method seems some way "not right"! I even called the /etc/init.d/hotplug script later during boot, just before gdm starts, but no way, the usb peripherals attached won't show up in the disk submenu. I even noticed that during boot it complains something with sda (and not the sda1 which is normally mi pendrive) that has "to assume write through"... I can't understand!
Is there a way to make this coldplug thing work?

Thank you

Tasu

---

### Post by jeremy on 2004-10-12
This isn't exactly answering your question, but I have a USB hd plugged into the back of my box, and on the hd enclosure there is an on/off switch - I just turn it on when I need it, without having to plug it in each time.

---

### Post by Anonymous on 2004-10-12
Ok! This could be a good point, And indeed even I could do this, but I'd like to have it all automated without the need to switch off/on or unplug/plug in order to get the device mounted...
As I said... I made an init script that could handle this, it updates the fstab at any restart if it finds new hardware on ide and usb/scsi, writing the right entry, so in the disk menu I always see the device... this is fairly what I want, but I think it would be a cleaner solution if the hotplug subsystem would handle this, and indeed, on their website, they say it's already this way... but... it's not!
I thought is a matter of when the hotplug script is called, but when I tried to call it later (ehm! almost latest! ^_^) It had no effect!

However... Thanx for the reply! ^_^

---

