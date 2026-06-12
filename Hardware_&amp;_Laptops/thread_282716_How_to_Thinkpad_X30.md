---
title: "How to: Thinkpad X30"
date: 2006-10-23
forum: Hardware &amp; Laptops
---

### Post by yurtboy on 2006-10-23
WARNING THIS IS A WORK IN PROGRESS PLEASE READ ALL ITEMS IN THIS THREAD BEFORE YOU TRY IT OR YOU MAY WASTE ALOT OF YOU TIME ( :
So far the only trouble, other then with the enduser(me), that I have dealt with is the wireless.
There are other issues I will work out and post in time.
For the wireless I added this to grub...
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet mem=425M **irqpoll**


Ignore the mem= this is due to a bad ram point.  This IRQPOLL seems to help with the wireless.  Though with further testing we will see.
Before this sometimes the os would not pick it up.
Also if I remeber right I set the bios to defaults which puts all IRQ/PIC on 11 though I think this has more to do with ISA?
Not to sure on this.
Al

---

### Post by yurtboy on 2006-10-31
Some more notes 
Suspend ie shut the lid and system goes to sleep and starts without a bunch of screen errors
blacklist....
rsrc_nonstatic
yenta_socket
pcmcia
pcmcia_core
sony_acpi

Wireless
Well most of the trouble was ME.
Overall it works fine, maybe out of the box fine, BUT I blacklisted 
orinoco_pci
and am using the hostap drivers for the nic (why? not sure)

---

### Post by yurtboy on 2006-11-02
One 
This is a great site to go to for Thinkpads and linux
[http://www.thinkwiki.org/wiki/ThinkWiki](http://www.thinkwiki.org/wiki/ThinkWiki)
Two...
My grub boot menu has been cleaned up a bit removing some earlier edits
basically my defoptions are what came with Ubuntu
Three....
Using lid to suspend cause mouse trouble ie my mouse became a big block.
So using KDE and clicking its suspend after adding this 
/etc/acpi/events/lid
Containing....
event=button/lid
action=/etc/acpi/actions/sleep.sh %e
And making it chmod 644 lid
Seems to help...I will test more when I get time

---

