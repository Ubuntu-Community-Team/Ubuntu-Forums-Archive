---
title: "How to remove a driver module ?"
date: 2005-11-23
forum: General Help
---

### Post by samir85 on 2005-11-23
Hey guys,

right now, I try to remove a driver module of my wireless card (which the system autoloads on every startup) in order to replace is with a newer driver. So I type "sudo rmmod rt2500.ko" and it works fine, but on next startup the driver is loadet again !
Can somebody tell how to prevent the driver from autoloading or how to completely uninstall the driver ? (the driver residents in ./lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/rt2500/rt2500.ko)


I'd appreciate any help

regards Samir

---

### Post by JustRandomName on 2005-11-23
I believe the more stable version of rmmod would be;

sudo modprobe -r rt2500

To stop the module loading at startup you need to add the module name to the blacklist. In a terminal type:

sudo gedit /etc/hotplug/blacklist

Then add the rt2500 to the list.

To be double sure you could do:

sudo gedit /etc/hotplug/blacklist.d/rt2500

And once again add the rt2500 to the file.

Hope this helps

---

### Post by samir85 on 2005-11-23
Thanks for you answer.

However, this is still not 100% clear to me. I'm afraid, that when I blacklist the driver module, my computer won't be able to load the new driver module too (because it has the same filename).

Isn't there some clean way to this ?
I mean there must be a file, where all modules, which will be autoloaded are listet. Can't I just change the filepath there from the old module to the new one ?

---

### Post by SickTwist on 2005-11-23
I'm pretty sure that when you install/compile a new version of the module it will overwrite the old one.

---

### Post by samir85 on 2005-11-24
[QUOTE=SickTwist]I'm pretty sure that when you install/compile a new version of the module it will overwrite the old one.[/QUOTE]

Well, I already tried that, but at every startup of the computer the old driver module is loadet.

Would be driver deleting the driver module in ./lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/rt2500/rt2500.ko a good possibility ? (or will get I get error on startup, because the system still tried to load the module ?)


Regards

---

### Post by aminalshmu on 2005-11-24
[QUOTE=SickTwist]I'm pretty sure that when you install/compile a new version of the module it will overwrite the old one.[/QUOTE]

this should be correct, if you are installing the same module with the same filename, for the same kernel.

if you don't want it to load at boot, look in the file /etc/modules and remove it.

---

### Post by samir85 on 2005-11-24
Ok, just to be sure:

My goal is to replace the old module (which is located in  ./lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/rt2500/rt2500.ko) with the new one. So I delete the old module and copy the new module to the location, where the old module resided ?

---

### Post by drakeoutlaw on 2005-12-02
[QUOTE=samir85]Ok, just to be sure:

My goal is to replace the old module (which is located in  ./lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/rt2500/rt2500.ko) with the new one. So I delete the old module and copy the new module to the location, where the old module resided ?[/QUOTE]


You are exactly correct. But I suggest you copy the old module somewhere else before overwriting it with the new one as a precaution.

---

### Post by samir85 on 2005-12-03
Thanks for the numerous replies,

now it works like a charm,


regards Samir ;)

---

