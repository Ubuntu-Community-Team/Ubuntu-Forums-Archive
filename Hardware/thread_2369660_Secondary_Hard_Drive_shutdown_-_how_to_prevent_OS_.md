---
title: "Secondary Hard Drive shutdown - how to prevent OS from accessing device"
date: 2017-08-25
forum: Hardware
---

### Post by Paul_Jewell on 2017-08-25
Hello All, 

I have a laptop with a secondary HDD and multiple other SSDs. The HDD is only used to dump seldom used files as an archive, however in general I want it powered down to save battery power. 

I have made a script to enable and disable the archive drive. To disable it looks like this:

```

#!/bin/bash
sudo umount /dev/sda1 
sudo hdparm -S 2 /dev/sda
sudo hdparm -Y /dev/sda

```

Even though everything relating to /dev/sda is unmounted, still once every few minutes (but more randomly, not at a fixed interval) the drive will spin up and the HDD light come on for a second. It seems something in ubuntu or the kernel has tried to check / access the drive. Is there anything else I can do to prevent this? Remove driver? Tell some linux/ubuntu service which drives to exclude?

Thanks for reading

---

