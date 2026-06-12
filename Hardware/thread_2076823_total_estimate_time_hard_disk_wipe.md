---
title: "total estimate time hard disk wipe"
date: 2012-10-27
forum: Hardware
---

### Post by ginmardo84 on 2012-10-27
does anyone have any idea how long it will take for a 250gb hard disk with a block size of 4096 take to be wiped to completely zeros? are talking an estimate of minutes or hours?

---

### Post by 2F4U on 2012-10-27
Depending on the speed of the drive and how many iterations you plan, it probably takes several hours.

---

### Post by ginmardo84 on 2012-10-27
> **2F4U said:**
> Depending on the speed of the drive and how many iterations you plan, it probably takes several hours.

 tell me about it. i just slept a good 2 hours through the process. thanks man.

---

### Post by amjjawad on 2012-10-28
The 'dd' command is very slow. Writing zeros to each and every sector/block of your HDD is not a fast operation at all. Some may consider this a low-level format (which is not really a low-level). It's different from formatting the HDD.

Some information about formatting: [http://en.wikipedia.org/wiki/Disk_formatting](http://en.wikipedia.org/wiki/Disk_formatting)

dd command: [http://en.wikipedia.org/wiki/Dd_(Unix](http://en.wikipedia.org/wiki/Dd_(Unix))

---

