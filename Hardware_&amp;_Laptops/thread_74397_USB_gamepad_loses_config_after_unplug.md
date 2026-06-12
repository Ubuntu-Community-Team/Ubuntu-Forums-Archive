---
title: "USB gamepad loses config after unplug"
date: 2005-10-11
forum: Hardware &amp; Laptops
---

### Post by molszewski8 on 2005-10-11
I have a MythTV setup with 4 USB gamepads that work perfectly (after spending 20 or so minutes setting up all the mappings in MAME, zsnes, fecu, etc.) However, when one or more of the controllers are unplugged then plugged in again, js0 button 1 is no longer the same controller/button it was previously. So pretty much unplugging one controllers makes all the remaining mappings useless. Is there any way to force static low-level mappings of joystick devices/button numbers upon plugin of the usb device? its really annoying to have to reconfigure across 3 different programs everytime something gets unplugged.

thanks in advance

---

### Post by poofyhairguy on 2005-10-12
Does this help?

[http://www.ubuntuforums.org/showthread.php?t=28538&highlight=usb+gamepad](http://www.ubuntuforums.org/showthread.php?t=28538&highlight=usb+gamepad)

---

### Post by molszewski8 on 2005-10-12
Thanks for the link...everything is working as it should. however my *problem* is that i want to somehow statically keep joystick device and button numbers, so i can unplug controllers if need be and still have them remap to /dev/input/js3 with button 4 being the "A" button. Right now if i unplug a gamepad and plug it back in i have to manually reconfigure zsnes to use the "new" joystick device and buttons.

---

