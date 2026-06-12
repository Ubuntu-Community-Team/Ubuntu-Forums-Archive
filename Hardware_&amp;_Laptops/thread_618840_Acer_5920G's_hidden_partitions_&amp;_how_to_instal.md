---
title: "Acer 5920G's hidden partitions &amp; how to install Gutsy?"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by plamen_todoroff on 2007-11-20
I got a new acer 5920g laptop with 250 GB hdd separated in two primary partitions. The shop assistent never told me that besides these two partitions there are two more hidden (also primary) partitions, one called PQSERVICE at the beginning of the hdd and one at the end of the hdd (no name). So now my hdd structure looks like that: 

1. pqservice, primary - hidden recovery partition - 10 GB
2. vista ntfs, visable, primary (C:) MAIN OPERATING SYSTEM - 110 GB
3. acerdata, ntfs, primary (D:) FOR DATA FILES, EMPTY - 110 GB
4. noname, primary - hidden partition, 4 GB, i googled around and found that there is windows xp installed in that 4-th partitions. It turns out that the laptop could be turned on in some "dvd-player-like state" for watching movies or listening to music without the vista being loaded. This is done by pressing a special button on the keyboard which booted that xp installation and some "Acer Arcade Deluxe" software running on it, thus achieving this dvd-player-like state".

MAIN GOAL:

I want to have vista on a smaller partition (60 GB) and to dual boot it with ubuntu. AND I want to keep that hidden partitions.


So, i'm thinking to wipe out C: and D:, i'll get 220 GB of unallocated space in the middle of the hdd, then i'll make one primary ntfs partition for vista. HDD partition state will be then like this:

1. hidden acer primary - still 10 GB
2. vista ntfs primary - now 60 GB
3. unallocated - now 160 GB
4. hidden "acer arcade deluxe" primary - still 4 GB

The only option for installing Gutsy is to make an extended partition in the unallocated space and in it the /boot, /, /swap, /home & a FAT32 partitions as logical partitions.

Should /boot & / be primary partitions for ubuntu to be able to boot? (Grub will be installed in MBR)? Will ubuntu see the hidden partitions and mount them? Will Grub see them too? What are they going to be named?

I'll really appreciate any suggestions about this delicate situation. Thanks.

---

### Post by gdzsi on 2007-11-21
Get yourself pqmagic, make your partitions. (delete them or resize the first if you want to keep it)
You can do it any way, but Windows needs a primary partition, but you can do the whole linux part in logical partitions. And consider that you don't have to have a separate /boot partion, you can have only a / and a swap.
The first OS to install should be windows, as it tends to kill Grub when installing.
When running the ubuntu installer, it will call them on their names when partitioning (you will have to select manual partitioning in order to keep your data). From their sizes and types, you'll know which partitions they are.

---

### Post by plamen_todoroff on 2007-11-23
I know all about grub and installing linux, i've did it about 10 times on my previous laptop, but it had no things like hidden partitions and i had the whole hdd "at the table".

So, if i understand you correctly none of the linux partitions need to be primary, is that right? Even a separate /boot partition? I want to have one as i like to keep things "organized". I've always had /boot, /, /home & /swap partitions and now that's my goal too, but now they all have to be logical because of these hidden primary partitions i have.

Thanks for your answer. No offence, but I'd like some more opinions on this subject for i'm pretty sure that /boot partitions must be primary, if not / too.

Anybody?

---

