---
title: "SWAP partition questions"
date: 2021-02-10
forum: Hardware
---

### Post by jmichaels29 on 2021-02-10
When doing a fresh install of 20.04, on my desktop, according to "Disks" app, no free space partition or swap partition was created on filesystem partition 2.  On my laptop when doing the same, a 1.1 MB Free Space partition was created.  The desktop has 8 gigs ram and laptop has 6 gigs ram.

Isn't it a good idea to have a swap partition?

If so, can it corrupt my data that is on partition 2 now?

Addendum: When running command "sudo swapon --show" I get similar results on both computers:


```

michael@michael-HP-EliteDesk-800-G1-SFF:~$ sudo swapon --show
[sudo] password for michael: 
NAME      TYPE SIZE USED PRIO
/swapfile file   2G 2.8M   -2
michael@michael-HP-EliteDesk-800-G1-SFF:~$ 

```

---

### Post by CelticWarrior on 2021-02-10
Ubuntu now uses by default a swapfile instead of a partition.

The 1.1MB free space isn't a partition. It happens in some drives for better partition alignment.

---

### Post by jmichaels29 on 2021-02-10
> **CelticWarrior said:**
> Ubuntu now uses by default a swapfile instead of a partition.

The 1.1MB free space isn't a partition. It happens in some drives for better partition alignment.

ok, thanks.

I added an addendum to my original post here.

---

### Post by Yellow Pasque on 2021-02-11
> **jmichaels29 said:**
> Isn't it a good idea to have a swap partition?
Generally, yes. That is why Ubuntu still creates a file for swap. The file can be resized as needed, but hopefully your systems have enough memory that they won't be using swap too much.

> If so, can it corrupt my data that is on partition 2 now?
This was more of a concern before journaled filesystems. If the swapfile is getting corrupted, you've got more serious hardware issues that would probably corrupt your filesystem anyway. One more reason for good backups..

---

