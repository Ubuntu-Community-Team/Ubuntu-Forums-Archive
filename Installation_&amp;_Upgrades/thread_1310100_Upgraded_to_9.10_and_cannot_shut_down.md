---
title: "Upgraded to 9.10 and cannot shut down"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by wizardus13 on 2009-11-01
Whenever I try to shut down, it shows the ubuntu symbol, but once that disappears it doesn't turn off until I shut it manually. Also I can't do anything when the screen turns black and it doesn't shut down.

This has happened since I upgraded to version 9.10. However, restarting seems to work fine.

---

### Post by ratcheer on 2009-11-01
Does this work from a terminal?

sudo init 0

Tim

---

### Post by wizardus13 on 2009-11-01
No, it does the same thing.

---

### Post by whoop on 2009-11-01
Do you have an old(er) mobo? maybe something like this helps:
Edit /etc/default/grub and add acpi=force to GRUB_CMDLINE_LINUX
and run update-grub2.

Or are you still using grub1? Then you need to edit menu.lst

---

### Post by wizardus13 on 2009-11-01
So should I install grub-pc? Right now I only have the grub package.

---

### Post by wizardus13 on 2009-11-01
OK I followed some instructions to update to GRUB2, and it seems to work, but it still fails to shut down.

Also, is there any problem in deleting the extra entries of previous kernel versions from the menu.lst thing?

---

### Post by ROY.G.BIV on 2009-11-01
Keep one or two older ones for troubleshooting reasons.

---

### Post by whoop on 2009-11-01
> **wizardus13 said:**
> OK I followed some instructions to update to GRUB2, and it seems to work, but it still fails to shut down.

Also, is there any problem in deleting the extra entries of previous kernel versions from the menu.lst thing?

Euh, grub2 does not use menu.lst. Remove the (unwanted) kernels via synaptic and they will disappear. Always leave a latest pair of working kernels as suggested.

---

### Post by rhackenb on 2009-11-01
Same here plus I get the "one or more disks are failing".  This happened as soon as I upgraded.

---

### Post by wizardus13 on 2009-11-01
All right. Thanks, it doesn't show the other kernels anymore.

I tried your first suggestion (acpi=force), and now I get something when shutting down:

> 
login: init: hal main process (699) terminated with status 1
init: avahi-daemon main process (713) terminated with status 255
modem-manager: Caught signal 15, shutting down...
init: Disconnected from system bus
[ lots of numbers] Power down.


Of course, it still doesn't shut down...

---

### Post by rhackenb on 2009-11-01
This works for me. 

sudo init 0

Why doesn't normal shutdown work?

---

### Post by wizardus13 on 2009-11-01
Hm... I think you have a different problem because that doesn't work for me either.

---

### Post by rhackenb on 2009-11-01
I noticed that I was having problems shutting down mythtv. This had been installed under 9.04. It always had problems running.  After I uninstalled and the used the "sudo init 0" to shut down, I could shut down the next time using the normal shut down menu.

---

### Post by wizardus13 on 2009-11-01
I don't have MythTV. I'm still getting the same message when I try to shut down, and it still doesn't shut down.

---

### Post by wizardus13 on 2009-11-01
By the way, I'm not using an old motherboard and its worked seamlessly in the past... but now I'm getting the output:

> 
login: init: hal main process (699) terminated with status 1
init: avahi-daemon main process (713) terminated with status 255
modem-manager: Caught signal 15, shutting down...
init: Disconnected from system bus
Power down.


---

### Post by wizardus13 on 2009-11-02
This is odd... it only showed that output the first time I shut down after I added acpi=force. Now it shuts down without any output (still doesn't actually power down).

---

