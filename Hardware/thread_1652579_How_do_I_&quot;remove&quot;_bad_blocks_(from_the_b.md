---
title: "How do I &quot;remove&quot; bad blocks (from the badblocks inode)"
date: 2010-12-25
forum: Hardware
---

### Post by Zakhafr on 2010-12-25
Hi all, and Merry Xmas!

I'm having trouble with my disk rack. I was using it in eSata and it reported a lot of read errors.

This errors show when I do

```
sudo dumpe2fs -b /dev/sdc1
```

Now that I realised that it comes from the rack and not from the disk itself (no problems in USB mode) I would like to "delete" the bad blocks declared in the badblock inode.

How am I supposed to do so (without reformating)?

Does it only adds badblocks to the existing one when you run badblocks?

---

### Post by Zakhafr on 2010-12-25
So apparently, running another "badblocks" command, even giving it an empty list of badblocks (-i option) do NOT remove the existing badblocks declaration.

Any idea on how to do that without the need of reformating?

---

### Post by Zakhafr on 2010-12-26
Auto-solved!

Debugfs + clear the inode #1 (clri)

---

