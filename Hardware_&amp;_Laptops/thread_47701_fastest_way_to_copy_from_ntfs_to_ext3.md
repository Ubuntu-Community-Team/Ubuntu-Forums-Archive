---
title: "fastest way to copy from ntfs to ext3 ?"
date: 2005-07-09
forum: Hardware &amp; Laptops
---

### Post by DarkManX4lf on 2005-07-09
i am trying to copy about 60gigs of files from a ntfs partition to a ext3 partition, whats the fastest way of doing that ?  i tried using the file browser and just dragging and dropping but it says there is 6hours remaining !!!!!

---

### Post by DarkManX4lf on 2005-07-09
anyone ?

---

### Post by DarkManX4lf on 2005-07-09
also moving files manually using the filebrowser seems to not work, after selecting everythign i want to copy and once i paste it starts to copy and then after a while i stops with no error....and plus while its copying the system becomes terribly slow.

---

### Post by banadushi on 2005-07-09
Personnaly, I would use rsync.  Open up a terminal and do:

```

$ rsync -av --stats --progess /path/to/ntfs/files /path/to/ext3/destination

```

If it bombs out for whatever reason, you can just re-run the command and it will pick up where it left off.

Have fun!

Jason

---

### Post by DarkManX4lf on 2005-07-09
so far its working nicely the bad thing is its lagging up my pc...

---

### Post by DarkManX4lf on 2005-07-10
how come when i try to transfer files from a ext3 drive to another ext3 drive its REALLY slow transfering ?  its terrible when it takes 5minutes to transfer 1gig worth of files....btw im trasfering from a sata drive to ide if that matters.

---

### Post by DarkManX4lf on 2005-07-10
i fixed the problem by enabling dma on hdb.

---

