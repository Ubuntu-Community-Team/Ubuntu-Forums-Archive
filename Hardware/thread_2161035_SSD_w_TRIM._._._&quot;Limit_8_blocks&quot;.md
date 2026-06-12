---
title: "SSD w/ TRIM. . . &quot;Limit 8 blocks&quot;?"
date: 2013-07-09
forum: Hardware
---

### Post by Byb on 2013-07-09
Hi all
I saw a closed thread about this question.
I'd like to discuss this. We see some ssd are lying about their geometry and I read that OS not able to be be more precise.
hdparm -I to my own ssd reports 512B/512B so I had the (false ?) idea that these minimum unit of 8 blocks could give a view of physical blocs (8*512=4K) if the drive doesn't lie here too.
But sectors are not blocs, and I read elsewhere that mlc ssds cannot trim such a little amount data, so the reported "TRIM supported (limit 8 blocks)" would be in this case a larger amount, e.g. 32k if 1bloc=4K.
My drive is a LMT-256M6M and no data-sheet is available, so I feel puzzled to just begin to try understanding concrete things in partitioning it the good way when all parted warnings about mis-alignment are not reliable if the drive lies.

Thank you for advises.

---

