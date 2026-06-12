---
title: "Logitech USB headset hangs lsusb on Edgy"
date: 2006-11-25
forum: Hardware &amp; Laptops
---

### Post by coreyfra on 2006-11-25
I installed Edgy last week.  I am attempting to use a Logitech USB headset.

The headset works fine initially, if I do a 'lsusb' it displays all of the USB devices on my system.  If I unplug the USB headset I can no longer do a 'lsusb'.  The command just hangs.  I can not Ctrl-C out of it.  If I plug the USB headset back in, the LED on it does not light up and it does not function properly again.

The USB system itself does not hang, I use a USB keyboard and mouse.

I check dmesg and there were no error messages when unplugging the headset.  Just a message about a USB disconnect.  One thing to note, I am not sure if this matters, the USB headset is the first USB device discovered during boot.

I have been able to reproduce this across multiple reboots.  I did one more test were I booted the system with out the headset plugged in.  At this time I can plug and unplug the headset and no issues arise.

I have the same problem on my Dell 8400 and my work laptop, a Dell D620.

---

### Post by teitunge on 2006-12-03
I have the very same problem. Just crossing my fingers for that someone knows how to deal with this. 

Restarting gnome is alright, but eventually it will become a frustrationmomento :)

---

