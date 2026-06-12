---
title: "[SOLVED] Paritions for a dual boot??"
date: 2008-08-22
forum: General Help
---

### Post by Yezinki on 2008-08-22
Whats the difference btw MiB & GiB?

1 MB =??

1 GB =??

Sorry to be such a pain........

Plan:

Vista NTFS:

1. 40GB Primary Active C partition.

2. 20 GB Logical D partition for Vista Data.

3. 20 GB /root Extended

4. 4 GB Linux swap.

5. 9 GB /home Extended

Total 93 GB for Dell XPS 1710 100 GB drive.

What do you think smart people??

---

### Post by Elfy on 2008-08-22
Could be a bit out - but a Gb is 1024Mb in RAM usually, 

You can only have 1 extended partition, 20Gb is big for / and 4Gb is probably to big for swap unless you have 4GbRAM and want to hibernate

I would

Primary - 40Gb Vista - under protest lol

Extended
Logical - 20Gb Vista data (which can also be used by buntu)
Logical - 10Gb / Linux
Logical - the remainder ~22.5Gb /home
Logical - 512Mb - but if size changes add it to /home

---

### Post by Too Late on 2008-08-22
> **Yezinki said:**
> Whats the difference btw MiB & GiB?

1 MB =??

1 GB =??
Umm... I'm not sure what you're asking, but:
1 MB = 1 000 000 bytes
1 GB = 1 000 000 000 bytes
1 MiB = 2^20 (= 1 048 576) bytes
1 GiB = 2^30 (= 1 073 741 824) bytes
and
1 B = 1 byte = 8 b = 8 bits.

---

### Post by Yezinki on 2008-08-22
Thanks for your comments forestpixie,

1. I have 4 GB of ram but never hibernate....so what should be size of swap..512 MB?

2. Vista Home premium 32 bit, MS office enterprise 07, with updates, service packs, utilities etc takes 21.7 GB.....with system restore off.

3. How do I proceed as you say I can have only 1 primary & 1 Extended partition.

4. Primary I can make while doing a clean Vista install.....it gives advanced drive option....so if that is used will it be logical or extended?

5. Supposedly I don't use that & install Vista on primary than I install Ubuntu using Live CD.....should I use Gparted to make the Extended & than 3 logical in it?

6. Should I give all space to extended or none?

Hoping to hear your experienced views....coz I am gonna start a dual now.

Regards!

---

### Post by Too Late on 2008-08-22
You can have four primary partitions. One of them can be an extended partition, which can contain many logical partitions.

---

### Post by Yezinki on 2008-08-22
How can I make 4 primary partitions??

---

### Post by Elfy on 2008-08-22
If I had a blank disk I would put vista on a primary at wathever size - then I would (this is just what I do) leave some unallocated space for whatever I want at a later date. Then with the remainder make an extended partition - say for instance a 200Gb hdd

50Gb - primary
140Gb - extended
10Gb - unallocated

Then make the logicals inside the extended

In yours frome above the 4 logicals all reside inside the extended , then you could if you so wished have anotheer 2 primaries.

If you have $gbRAm and never hibernate then yes 512MB of swap should suffice.

The size of the extended can be as much or as little of the space left after the primary - obviously it has to be big enough - but there is nothing to stop you having unallocated space within it.

Perhaps make the 40Gb primary for the vista install - then do the rest of the partitioning with gparted - it will do all your partitioning including the data one for vista in ntfs.

To be completely honest there are as many permutations as you could wnat - it depends on what you want really. Bu tI would stick with the plan I gave above - I'll edit ti to take account pf the swap.

---

### Post by Yezinki on 2008-08-22
Says No root file system defined.

Please correct this from the partitioning menu??

Now I have used G parted to create the extended & 4 logical.

But on install get this display error??

---

### Post by Elfy on 2008-08-22
I assume you are doingit manually - highlight the partition you intend to install to - near bottom of screen - edit button. You go to new screen - I think that you have to tell it use the partition - choose as ext3 and thenere should be a dropdown menu for mountpoint - pick /

Do the same for the partition you have for /home and give that a mountpoint of /home

---

### Post by Yezinki on 2008-08-22
Yes I am doing it manually.......I did as you suggested....You are the most concise, accurate, prompt, humble member I have yet met.

Dont beat about the bush......know exactly what you are talking about.

Thanks alot you made my day...........

Always welcome.........im a med doc.

Regards!

---

### Post by Yezinki on 2008-08-22
You actually made me practice practically to make partitions / sizes for a dual boot.

Thanks again......but I might keep bothering you new to the world of Ubuntu.

Btw Kubuntu Hardy Heron 8.0.4.1 is the same as Ubuntu with a different look .....same platform??

---

### Post by Elfy on 2008-08-22
Well thank you very much!! - you've just made my night :lol: - enjoy it

One more thing you can do is mark thread solved - thread tools :D

---

### Post by Yezinki on 2008-08-22
Thanks & sleep sound.

I will..........

---

### Post by Yezinki on 2008-08-23
Screen shot of my drives dual boot!

---

