---
title: "Saved folder in ubuntu cannot read in XP"
date: 2008-08-09
forum: General Help
---

### Post by Otpadnik on 2008-08-09
Hi,
I have a problem and I would really like to find a solution.

I am dual booting XP and Ubuntu and under ubuntu I've downloaded a couple of old-time games on NTFS partition using azureus.

From ubuntu I can access downloaded folders, mount images and everything.
But, from WinXP I can access some folders and some I cannot.
I've tried to copy unreadable folders to another NTFS partition, but they emain unreadable.
In XP I've installed ISF Drives if it means anything.

This isn't such a huge problem, I could of course burn images to CD and then (I guess) read them from XP, but I'm really curious to find out whats wrong with this.

Thanks,
Otpadnik

---

### Post by Otpadnik on 2008-08-09
Ok,
After two days of hadache only 12minutes after I've posted question I've realised what was a problem.
Ubuntu allows to save folder on NTFS partiotions using characters like ':', ',', ...
And thats what I did, I've saved folders and named them with ':' so under XP they were unreadable.
Now I've went back to Ubuntu, renamed folders in something more "normal" and voala! It works :)

Best wishes,
Otpadnik

---

