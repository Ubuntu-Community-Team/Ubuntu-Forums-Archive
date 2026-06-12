---
title: "When I shutdown, the computer stays on"
date: 2012-03-09
forum: Hardware
---

### Post by Her Tigger on 2012-03-09
When I boot up Ubuntu or shutdown/sleep/hibernate I get a weird display of stripes that almost make out words but it's a bunch of stripes and parts change to :) ;( :} and other symbols. However when I shutdown/hibernate I can hear the hdd and fans shutdown but I have then stripes 2 manually turn the computer off. I have Ubuntu on a Hewlett Packard Pavilion 4535 w the only upgrades of 510 ram, a 117 gb hdd and a LG cdr-w. If u need screen shots of the boot screen or any info to help me solve this problem, plz let me know.

---

### Post by plucky on 2012-03-10
> **Her Tigger said:**
> When I boot up Ubuntu or shutdown/sleep/hibernate I get a weird display of stripes that almost make out words but it's a bunch of stripes and parts change to :) ;( :} and other symbols. However when I shutdown/hibernate I can hear the hdd and fans shutdown but I have then stripes 2 manually turn the computer off. I have Ubuntu on a Hewlett Packard Pavilion 4535 w the only upgrades of 510 ram, a 117 gb hdd and a LG cdr-w. If u need screen shots of the boot screen or any info to help me solve this problem, plz let me know.

Edit the file /etc/default/grub and add the parameter acpi=force into the line ```
GRUB_CMDLINE_LINUX="acpi=force"
``` then run ```
sudo update-grub
``` to update grub and after you reboot,see if the system now shuts down.

You might be better off running Lubuntu on your system.

Good Luck

---

