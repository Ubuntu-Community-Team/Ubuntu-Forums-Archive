---
title: "Unable to edit &quot;nr_requests&quot; via echo"
date: 2008-12-19
forum: Hardware
---

### Post by caveman8 on 2008-12-19
I'm trying to change the string within "/sys/block/sda/queue/nr_requests" from 128 to 512 in order to improve performance of a recently installed 3ware hw RAID controller. Whenever I attempt to do so I get an error message indicating a permission issue.

I am able to edit the file directly if I open it with an editor.

Below is the command I used and the result:

joe@hilltop:/$ sudo echo 512 > /sys/block/sda/queue/nr_requests
-bash: /sys/block/sda/queue/nr_requests: Permission denied

Thanks for any assistance. I suspect I'm making some simple mistake in syntax, etc.

I'm running Ubuntu server 8.04, 64 bit.

Thanks again,

Caveman8

---

