---
title: "MP3 Player Mystery - Can you solve it"
date: 2008-09-28
forum: General Help
---

### Post by cnbiz850 on 2008-09-28
Below is copied from an unsolved topic.  I have the same problem now only with a different mp3 player and a 1GB disk instead.  In my case, the disk goes to about 412MB and Nautilus reports that it is full.

Can anyone please help solve this problem?

===============
Okay here is a wild and wooly one for someone to solve.

I have an MPIO music player (2 gig.) It is formatted FAT.

I can use 25% of the space. After that Linux says it is full and I can no longer transfer any music. If I fire up windows - everything works fine.

Why is LINUX telling me that there is space left - tons of it and rightfully so.... and why could I transfer up to 25% of the disk and now I cannot?:popcorn:

The device is brand new. I started to transfer music. After transfering about 100 songs it gave me the "device is full warning". I booted into Windows. I transfered another 20 songs. I went back into Linux same problem. Then I tried to delete one file. That worked.

---

### Post by lian1238 on 2008-09-28
Did you happen to delete files from the MP3 player from Ubuntu? If so, they will still be in a hidden folder ".Trash-yourname". Press Ctrl+H to unhide and shift+delete the folder.

If, however, that's not the case, try gparted. Install it if you don't have it yet. It's a partition editor. Look at your mp3 player with gparted and see the free space. Is it correct?

---

### Post by cnbiz850 on 2008-09-29
> **lian1238 said:**
> Did you happen to delete files from the MP3 player from Ubuntu? If so, they will still be in a hidden folder ".Trash-yourname". Press Ctrl+H to unhide and shift+delete the folder.
[\quote]
i haven't deleted files as it is brand new.

[quote]If, however, that's not the case, try gparted. Install it if you don't have it yet. It's a partition editor. Look at your mp3 player with gparted and see the free space. Is it correct?

the size from nautilus property is correct -- 1GB.  Don't know what reason it won't copy files onto it above 412mb.

---

### Post by jonian_g on 2008-09-29
Format the mp3 player to fat32.

---

### Post by cnbiz850 on 2008-09-30
Well, I guess my case was dur to a faulty player.  Now the retailer changed a new unit for me and it works fine.  No problem.  Sorry for the trouble.

---

