---
title: "120 GB SSD 110 GB available, plus a very interesting problem"
date: 2011-01-14
forum: Hardware
---

### Post by deltacomp on 2011-01-14
Hello, I have a HP 2540P laptop which I upgraded with a OCZ Vertex 2 120 GB SSD, installed Ubuntu 10.10 without a problem (no swap/upgraded memory to 8GB). I then followed a guide which allowed me to disable journaling (as far as I can tell I have enabled "TRIM" after completing the guide). 

What I found later was that the system shows only 110 GB total, and 100 GB of available storage?!?!? Some questions I have asked my self: Is there a swap on there? When I check fdisk -l in terminal it shows total capacity of ~120 GB but again it shows 100 GB available, with no swap area/partition, so again where did the other 20 GB go?

Now the very interesting part, I noticed a couple days ago that after an update and a restart, the same update was available for download. I found this kind of strange, so I did some more checking and found that a lot of changes to files and new programs were also not saved on the system. After several attempts to save anything on the computer, I realized that after every restart, it would default back to a certain period/environment regardless of the changes. 

After spending several hours trying different things, changing the back round, colors, etc... I decided to reinstall Ubuntu. After reformatting the SSD and installing a fresh version of 10.10, I found that the SSD was still only showing 100 GB available (again no swap). Then after I tweaked the environment, I shut it down, turned it back on a while later and KAPOW!!! back to the old environment!!! I couldn't believe it, but some how after reformatting the SSD, the original environment was back. I ask my self if there is some partition in the SSD which is not showing up in fdsik -l and gparted that is storing this configuration and loading it as a default after every restart? If so how do I annihilate it? 

I have been searching several forums for some information on removing swaps and expanding SSDs but have come up empty. Any help would be greatly appreciated. 

Thanks in advance.

---

