---
title: "painful driver update experience...."
date: 2011-01-23
forum: Hardware
---

### Post by u-noob-tu on 2011-01-23
i actually wrecked my display/graphics drivers and had to reinstall ubuntu. what i want to do is update the driver for my intel GMA x3100 card. intel pointed to a site called [http://intellinuxgraphics.org/](http://intellinuxgraphics.org/) where i found the 2010 Q4 driver package. well, package isnt really the word, its a bunch of stuff you have to compile yourself. before i wrecked my drivers, i had given it a shot, and when i rebooted, my screen had gone wonkers and i couldnt do anything. the REASON i want to update the driver is i get bad performance from the open source driver (compiz stutters a lot, plus some windows games wont run because of poor 3d support). i am very hesitant to try the install myself again. i need some professional advice. if there is an easier way, then PLEASE let me know, or if you can give baby steps, that would be great too.

---

### Post by u-noob-tu on 2011-01-24
gentle *BUMP*

---

### Post by u-noob-tu on 2011-01-24
okay, new question: i was looking around in the system logs when i took a look at jockey.log and saw a lot of interesting things. a lot of messages having to do with repository update failures, like this: ```
DEBUG: Updating repository indexes...
2011-01-23 22:20:50,060 DEBUG: ... fail!
``` and ```
Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-01-23 22:21:05,727 WARNING: _detect_handlers(): No package repositories available, skipping check
2011-01-23 22:21:05,766 WARNING: new_used_available(): No package repositories available, skipping check
2011-01-23 22:22:59,237 DEBUG: Updating repository indexes...
2011-01-23 22:22:59,332 DEBUG: ... fail!
2011-01-23 22:23:04,166 DEBUG: Shutting down
```

it looks like jockey isnt able to find any proprietary drivers. that seems strange, because when i installed ubuntu it did show two wireless drivers, though i only needed one of them. this might be the solution to my driver issue. if it will show up in jockey, then i can install painlessly. any suggestions?

---

