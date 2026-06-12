---
title: "Reinstalling while keeping existing /home and other partitions"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by ejunooni on 2009-01-18
Hello folks,

I want to re-install ubuntu 8.10 but I want to keep my /home and other partitions intact. I have the following set up right now.

```
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1eaf0fda-8a07-4f08-9690-f485d8d3cf18 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=7d59e2f5-a6e5-4a04-9594-983b26c3c5c6 /boot           ext3    relatime        0       2
# /dev/sda7
UUID=f0ac3277-7fc9-44c6-9423-5ce786fadaaa /home           ext3    relatime        0       2
# /dev/sda8
UUID=ba1f5612-ae40-4a0c-9107-712eb0536522 /tmp            ext3    relatime        0       2
# /dev/sda9
UUID=6507ba96-ccda-46f6-b136-5faf4a8ff0d5 /vmware         ext3    relatime        0       2
# /dev/sda5
UUID=bd453327-5f60-4d5f-aeae-a6c2be395645 none            swap    sw              0       0
```

From what I understand, when re-installing, I'll have to select the / mount point to re-install the OS and select to format it. For the rest of the partition I'll just select the same mount points as existing (e.g I'll select /dev/sda7 to be /home) but not format it so that the data remains. Is this correct?

Also, should I format any other partitions such as swap, boot etc? 

Thanks

---

### Post by taurus on 2009-01-18
Pick the Manual option when you get to the partition screen and make sure you mount the right device to the right mount point.  You don't have to format /home if you want to keep all your data and swap partition will be formatted according since there is nothing on it anyway.

If you want a clean system, I would recommend you format everything except /home.

---

