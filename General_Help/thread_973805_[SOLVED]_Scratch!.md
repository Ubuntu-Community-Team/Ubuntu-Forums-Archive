---
title: "[SOLVED] Scratch!"
date: 2008-11-07
forum: General Help
---

### Post by Yezinki on 2008-11-07
Hello every one,

I have Ubuntu 8.10 installed on my Sony Vaio VGC-LS1.

I'm going to reinstall with a dual boot with XP MCE.

HD is 250 GB.

What should be the partitioning strategy &  file systems?

All suggestions are welcome.

Regards,

Yezinki.

---

### Post by anystupidname on 2008-11-07
You should probably decide this for yourself. We don't know much about your intentions. Since you will be installing MCE, you'll probably want a huge (shared?) partition for video/audio data. But then again, you might be putting your data on a NAS device... So um, 10GB for nix, 15GB for XP MCE, small swap partition if you want it, and a huge shared partition with the rest of the space...? Unfortunately, XP pretty much forces you to use NTFS for the large shared partition otherwise I might suggest JFS/XFS for that partition. EXT or reiser for the nix partition.

---

### Post by Yezinki on 2008-11-07
What I had in mind was:

1. Primary NTFS: 50 GB

2. Logical NTFS: 100 GB

3. Logical / : 20 GB.......file system I don't know

4. /home: 50 GB

5. /swap: 5112 MB or 1 GB

Resize this plan if you like.........


Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-07
> **ilkolinux said:**
> well the best thing would be to put a 512mb or 1gb swap space, lets say something between 10-20gb for ubuntu and xp each respecitvely, one on ntfs and one on ext3, and a large shared which has to be ntfs/fat32 so xp can use it also.

Can XP & Ubuntu share a NTFS partition?

Regards!

Yezinki.

---

### Post by anystupidname on 2008-11-07
> **Yezinki said:**
> Can XP & Ubuntu share a NTFS partition?

Regards!

Yezinki.

Yes.

---

### Post by Yezinki on 2008-11-07
Hi there thanks for answering.

What would be yours plan for a dual boot of XP MCE & Ubuntu on a 250 GB HD?

Regards,

Yezinki.

---

### Post by anystupidname on 2008-11-07
> **Yezinki said:**
> Hi there thanks for answering.

What would be yours plan for a dual boot of XP MCE & Ubuntu on a 250 GB HD?

Regards,

Yezinki.

Um, if you're talking to me, I already answered that question. I was the first person to answer your post/question.

---

