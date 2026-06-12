---
title: "[SOLVED] External hard drive space being recorded incorrectly?"
date: 2008-09-24
forum: General Help
---

### Post by Replicon on 2008-09-24
It looks like df is miscalculating something...

```

df -h 
Filesystem            Size  Used Avail Use% Mounted on
...
/dev/sdb1             925G  200M  878G   1% /media/disk

```

erm... 925GB - 200MB != 878GB

Is this a known issue with df, or is my HD being funky?

thanks

---

### Post by plucky on 2008-09-25
> **Replicon said:**
> It looks like df is miscalculating something...

```

df -h 
Filesystem            Size  Used Avail Use% Mounted on
...
/dev/sdb1             925G  200M  878G   1% /media/disk

```

erm... 925GB - 200MB != 878GB

Is this a known issue with df, or is my HD being funky?

thanks

If this filesystem is ext3, then 5% is reserved for root and is not available to the user.

5% of 925G = 46.25   and 925G - 46G = 879G which is what df is showing.


Good Luck

---

### Post by Replicon on 2008-09-25
That explains it, thanks a lot.

---

### Post by unutbu on 2008-09-25
I'm just curious Replicon: would please post the output of
```

df                         # Shows sizes in 1K-blocks
sudo tune2fs -l /dev/sdb1  # Reports reserved space in 4K-blocks

```

I have been operating under the belief that df reports total, used and available space, and that 
```

total = used + available + reserved
```

If this is so, then there is something funky about your HD.

The tune2fs command will show in its output how many blocks are reserved.
Using the output of the two commands we should be able to account for each and every 1K-block. At least that has been my experience. Yours is showing that something interesting is going on, since 925 < 200 + 878 + reserved.

---

