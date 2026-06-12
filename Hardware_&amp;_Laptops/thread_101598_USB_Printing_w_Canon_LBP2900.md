---
title: "USB Printing w\ Canon LBP2900"
date: 2005-12-10
forum: Hardware &amp; Laptops
---

### Post by phreeza on 2005-12-10
Hi there,

I installed Breezy Badger 2 days ago after a long break from Linux, and everything is working fine, except for this one thing:

I have an LBP 2900 hooked up via USB. If it is switched on before startup it gets recognized and all, and i have installed the Driver provided by Canon on the website.Everything looks fine but the command to print a test page doesn't cause the slightest reaction by the printer. The logfile contains the same entry, repeated over and over again:

```

Dec 10 03:35:09 localhost kernel: [4296772.588000] drivers/usb/class/usblp.c: usblp0: error -32 reading printer status

```

The Gnome client doesn't give any error message. 

Hotplugging the printer doesn't seem to work either, the printer seems to get recognized by the hotplug system and the printer shows up on lsusb, but the Gnome client doesn't seem to recognize the printers presence.

yep, i think thats about all i can tell you, I'd be really greatful for any troubleshhoting advice...

Thomas

PS: I have also tried to change the permissions of /dev/usb/lp0, but to no avail...

---

### Post by tora201 on 2005-12-28
Did you manage to get it going? The LBP series of printers (I have a LBP 1210) seem to be a hopeless cause.....
If anybody has ever managed to get an LBP series printer going in Linux, please do let us know how!

---

### Post by krokodil on 2006-08-08
[http://www.ubuntuforums.org/showthread.php?p=1356211](http://www.ubuntuforums.org/showthread.php?p=1356211)

---

### Post by RussianMan on 2008-03-30
All greetings! 
I have printer Canon 2900 adjusted on [this](http://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900) How-To.
It ceases to work after an output from hiberante.
I am am helped by a command: sudo/etc/init.d/ccpd restart
How to make that it it was carried out automatically after hiberante a computer?

At me Ubuntu 7.10 At a Russian-speaking forum to me anything could not advise. 
And I badly write in English :-(

---

### Post by RussianMan on 2008-04-05
> **RussianMan said:**
> All greetings! 
I have printer Canon 2900 adjusted on [this](http://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900) How-To.
It ceases to work after an output from hiberante.
I am am helped by a command: sudo/etc/init.d/ccpd restart
How to make that it it was carried out automatically after hiberante a computer?

At me Ubuntu 7.10 At a Russian-speaking forum to me anything could not advise. 
And I badly write in English :-(

Answer: [http://ubuntuforums.org/showthread.php?p=4617431#post4617431](http://ubuntuforums.org/showthread.php?p=4617431#post4617431)

---

