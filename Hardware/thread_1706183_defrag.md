---
title: "defrag"
date: 2011-03-13
forum: Hardware
---

### Post by avatarmonkeykirby on 2011-03-13
Now hold on, before people start jumping down by throat about how "you don't have to defrag linux" just give me a moment to explain. I understand that EXT3 and up are journaled systems that don't have to be defraged and if I wanted all I would have to do is move the file away from the drive and then back. However in this case I'm on a solid-state drive using EXT2 (which is NOT journaled) to save the flash chip from wasting write erase cycles.

Please, no holy wars. Just tell me how to do it.

---

### Post by vanadium on 2011-03-13
It will be the same approach. Moving the data away and back. Also defrag tools, in as far as they exist and are reliable, would need to move data. If your consideration is to minimize writing to the solid state drive, I don't think that a dedicated defrag tool would make a difference in that respect over moving/recopying the data.

---

### Post by avatarmonkeykirby on 2011-03-13
> **vanadium said:**
> It will be the same approach. Moving the data away and back. Also defrag tools, in as far as they exist and are reliable, would need to move data. If your consideration is to minimize writing to the solid state drive, I don't think that a dedicated defrag tool would make a difference in that respect over moving/recopying the data.

Well that's good to know that it would still work on EXT2, but that's still not an option in this case. I don't have a large enough drive to move the files to before moving them back.

---

### Post by MyR on 2011-03-13
Are you experiencing performance issues that you know are related to file fragmentation?

I think vanadium's main point was that if you're trying to minimize read/write cycles to disk, defragmenting is NOT what you want to do.

---

### Post by vanadium on 2011-03-13
That restriction was not clear from your question. Anyway, I presume you have backups of your data.

---

### Post by avatarmonkeykirby on 2011-03-13
> **vanadium said:**
> That restriction was not clear from your question. Anyway, I presume you have backups of your data.

Yes, I do have backups of the vital data I need. If you know of anything that would be great.

---

