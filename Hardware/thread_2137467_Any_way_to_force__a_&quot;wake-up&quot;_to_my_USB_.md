---
title: "Any way to force  a &quot;wake-up&quot; to my USB trackball?"
date: 2013-04-20
forum: Hardware
---

### Post by alhefner on 2013-04-20
I have a logitech wireless trackball. When Ubuntu first starts, it is not working but, if I pull out the receiver from the USB port, let it sit for a few seconds, then plug it back in, it works just fine and will work normally until I shut down.

I was wondering if there is some driver or modification to the setting I can use to kind of wake it up so I don't have to unplug then plug it back in to get it going.

---

### Post by alhefner on 2013-04-22
Anyone?

---

### Post by kurt18947 on 2013-04-23
This is strictly a guess based on a similar problem with a USB wifi adapter.  The fix for that problem is to create a file that suspends the module prior to the machine going into suspend.  Then when the machine wakes up the module will 'wake up' and all is well.  You'll need to determine which module loads when you insert the USB adapter for your wireless trackball.  It may be something along the lines of "logitech_hid_" something or other.  You could open a terminal, type "lsmod" and look at the results, see if there's a likely candidate.  Possibly opening a terminal, type "dmesg" remove and reinsert the receiver and see if there are any clues about the module (driver)in dmesg.  Here is the fix I use on a new install when I want a certain USB Wifi adapter to suspend and resume properly.


[LIST=1]
[*]Log on as a SUDO user, you're editing a system file. 
[*]Open  a terminal or navigate via the GUI.  In terminal enter "sudo gedit  /etc/pm/config.d/config."  A new blank text editor page will open. 
[*]Enter this one line including caps, underscore  and quotes. :  SUSPEND_MODULES="<module name here>". 
[*]Save and exit. 
[*]reboot 
[/LIST]

Am I certain this will work for you?  No.  It's something to try, though.  If it doesn't work, delete what you just did and no harm.

---

### Post by alhefner on 2013-04-23
Hmmm "lsmod" output is the same, other than the order in which the modules are listed, when trackball is working and when it isn't...

Sometimes the trackball works right away though. Sometimes, I have to unplug the reciever then plug it back in...

Doesn't *seem* to have anything to do with the system suspend function...

---

### Post by tgalati4 on 2013-04-23
Put the module in /etc/modules.  That will load it by force at every boot.  If it still doesn't work, then try the following:

Search for *acpitool* in the forums.  You can use it to keep a USB port powered after shutdown.  Your trackball probably has a small processor that takes some time to boot and it not ready by the time the kernel is looking for new devices.  If *acpitool* does not work, then perhaps use a custom udev rule to load the correct module.

Also check your BIOS--"Allow USB devices to Wake" and "Support Legacy USB devices".  This will provide power to those devices immediately at power-on so that there is a better chance for device detection.  You might benefit from flashing your BIOS to the latest if there is a BIOS bug that is preventing your hardware from being detected.

---

