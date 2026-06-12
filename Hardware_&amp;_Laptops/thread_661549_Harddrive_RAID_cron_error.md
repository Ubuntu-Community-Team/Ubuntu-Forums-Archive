---
title: "Harddrive RAID cron error"
date: 2008-01-08
forum: Hardware &amp; Laptops
---

### Post by cov on 2008-01-08
I'm getting the following daily message from the system:```



From root@base Tue Jan 08 07:36:08 2008
Return-path: <root@base>
Envelope-to: root@base
Delivery-date: Tue, 08 Jan 2008 07:36:08 +0200
Received: from root by Base with local (Exim 4.67)
        (envelope-from <root@base>)
        id 1JC78C-0002rx-0A
        for root@base; Tue, 08 Jan 2008 07:36:08 +0200
From: Anacron <root@base>
To: root@base
Subject: Anacron job 'cron.daily' on Base
Message-Id: <E1JC78C-0002rx-0A@Base>
Date: Tue, 08 Jan 2008 07:36:08 +0200
Status: RO

/etc/cron.daily/system-health:

/bin/cat: /proc/mdstat: No such file or directory
sh: /usr/bin/sensors: not found

*** System health report ***

System RAID:


```

I don't have RAID, just Gutsy on hdb1, swap on hdb2 and /home on hdb3.

---

### Post by Windsurfer619 on 2008-06-25
I'm getting the same. Have you managed to figure out the cause?
Sorry I'm bringing up such an old topic.

---

