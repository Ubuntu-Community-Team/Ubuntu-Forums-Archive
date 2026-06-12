---
title: "fatal boot error inserting pciehp, shpchp by modprobe ?"
date: 2005-03-20
forum: Hardware &amp; Laptops
---

### Post by secristrc on 2005-03-20
On boot my system takes a long time pausing at:

[FONT=Courier new]modprobe: FATAL: Error inserting pciehp (/lib/modules/2.6.8.0.1-3-386/kernel/drive
rs/pci/hotplug/pciehp.ko): Operation not permitted

modprobe: FATAL: Error inserting shpchp (/lib/modules/2.6.8.0.1-3-386/kernel/drive
rs/pci/hotplug/shpcp.ko): Operation not permitted[/FONT]

Where do I go to find out what these modules are and how to take them out of the boot sequence ?

Thanks,
rcs

---

### Post by telmo on 2005-03-20
I'm not sure where, but the answer is somewhere in this forum...
Just use the Search button and look for pciehp shpchp.

I think you should add them to the blacklist. I don't really remember how... But it's nothing serious.

---

### Post by Buffalo Soldier on 2005-03-20
This is one of the most frequent asked questions and it's already answered here in the forum and at [UbuntuGuide.org](http://ubuntuguide.org). The direct link is [http://ubuntuguide.org/#modprobefatalerror](http://ubuntuguide.org/#modprobefatalerror)

---

### Post by secristrc on 2005-03-21
A most cool resource I was not aware of -- thank you kindly !

rcs

---

### Post by gasparov on 2005-03-24
[QUOTE=secristrc]A most cool resource I was not aware of -- thank you kindly !

rcs[/QUOTE]
 I solved booting the system problerly without blacklisting:nolapic and noapic at boot

---

### Post by amadeov on 2007-07-02
Just as a sidenote, I'm stuck in the middle of this problem currently and that link provided by the mod does NOT WORK ANYMORE.  I understand that it's an old post... so, when I find out what I can to fix this, I'll try to post a more recent solution!

The correct answer is:

Add a line for each failed module to ```
/etc/hotplug/blacklist
```, e.g., in my case adding ```
shpchp
``` to the blacklist.  When I rebooted, my laptop came up fine. =)

---

