---
title: "shutdown system beep in intrepid"
date: 2008-11-23
forum: General Help
---

### Post by josel777 on 2008-11-23
I have read several treads about disabling the system beep during shutdown.

I get the following with "sudo rmmod pcspkr": ERROR: Module pcspkr does not exist in /proc/modules. However, sudo modprobe -r pcspkr works each time I run it.

When I add "blacklist pcspkr" to "/etc/modprobe.d/blacklist" the beep doesn't go away permanently. Below are the contents of "/etc/modprobe.d/blacklist":

[COLOR="Navy"]cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# slow wireless driver
blacklist bcm43xx

# this is how you mute annoying beeps in console and shutdown
blacklist pcspkr[/COLOR]

What am I missing?

---

### Post by josel777 on 2008-12-14
Still unresolved.

---

### Post by frankleeee on 2008-12-14
I suspect this can be fixed in system-preference-sound it may be disable alert sound. Sorry tried this and several other disables' and nothing worked (never mind)

---

### Post by josel777 on 2008-12-17
> **frankleeee said:**
> I suspect this can be fixed in system-preference-sound it may be disable alert sound. Sorry tried this and several other disables' and nothing worked (never mind)

Thanks for trying to help. I am not sure why my laptop keeps on beeping when I shut it down. It is very annoying.

---

