---
title: "Hardware Information without opening the PC"
date: 2007-11-08
forum: Hardware &amp; Laptops
---

### Post by Nighto on 2007-11-08
Hi,

years ago, when I used to run that OS from Microsoft, I run programs like AIDA32/Everest, Sandra or CPU-Z if i wanted to know something about the PC i was using, such as memory speed, motherboard name etc. Is there any programs to do such task on Linux?

I made a nice script to gather some of that information, but don't know what would be the next steps.

```

#!/bin/sh
# Mariana Is Not Everest by Nighto, 2007
echo "M.I.N.E. - Mariana Is Not Everest"
echo " "
echo "Processor: `cat /proc/cpuinfo | grep model\ name | cut -f2 -d: | cut -c2- | tr -s " "a`"
echo "Cache: `cat /proc/cpuinfo | grep cache\ size | cut -f2 -d: | cut -c2-`"
echo "RAM:`cat /proc/meminfo | grep MemTotal | cut -f2 -d: | tr -s " "a`"
echo "HD: `hddtemp /dev/sda | cut -f2 -d: | cut -c2-` ($(echo "scale=2; `cat /proc/partitions | grep sda$ | tr -s " "a | cut -d" " -f4` * 1024 / 1000000000" | bc) GB / $(echo "scale=2; `cat /proc/partitions | grep sda$ | tr -s " "a | cut -d" " -f4` / 1048576 " | bc) GiB)"

```

(save as "mine", mark as executable ("chmod +x mine") and run it as root ("sudo ./mine"). Also note that you should have hddtemp installed, so if you don't have it, install it with "sudo apt-get install hddtemp")

---

### Post by ccprog on 2007-11-08
Try using hal-device-manager

It should also be available via the settings menu under the name "Hardware Information"

---

### Post by Nighto on 2007-11-08
> **ccprog said:**
> Try using hal-device-manager

It should also be available via the settings menu under the name "Hardware Information"

I know that program, but it doesn't show things like the motherboard name, or the memory velocity.
Any idea of how accomplish this?

---

### Post by dabl on 2007-11-08
Here's some stuff that might help:

[http://www.computerbob.com/guests/how_to_get_system_info_in_linux.php](http://www.computerbob.com/guests/how_to_get_system_info_in_linux.php)


I think dmidecode will do a lot of what you have in mind.


:)

---

### Post by Nighto on 2007-11-08
> **dabl said:**
> Here's some stuff that might help:

[http://www.computerbob.com/guests/how_to_get_system_info_in_linux.php](http://www.computerbob.com/guests/how_to_get_system_info_in_linux.php)


I think dmidecode will do a lot of what you have in mind.


:)

Nice page. I'm gonna look over dmidecode and will come back here with results.

Thanks!

---

