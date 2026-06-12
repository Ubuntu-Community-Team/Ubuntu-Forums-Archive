---
title: "One Device Name Has Two UUID's"
date: 2008-11-27
forum: Hardware
---

### Post by Rexcellent on 2008-11-27
Perhaps I should be posting this in a more general Linux forum, but I've become such a fan of Ubuntu, so here it goes:

I issued the following command with the abbreviated results:
```
root@server:/# blkid
...
/dev/md0: UUID="5fde8b84-49d1-4a52-b9a9-3cdbf432ab1d" TYPE="ext3"

```

Then I issued:
```
root@server:/# mdadm --detail --scan
...
ARRAY /dev/md0 level=raid5 num-devices=4 metadata=00.90 UUID=0d0152dd:d6532c83:bd94c120:a359ab0a

```

So my question is why does /dev/md0 have two different UUID's?

My guess would be that it's the difference between the array and the filesystem, but is there a more technical explanation?

Cheers,
Rex

---

