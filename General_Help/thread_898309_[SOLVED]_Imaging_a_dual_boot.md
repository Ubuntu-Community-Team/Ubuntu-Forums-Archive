---
title: "[SOLVED] Imaging a dual boot?"
date: 2008-08-23
forum: General Help
---

### Post by Yezinki on 2008-08-23
Hi there,

Am in my neonatal period, in the world of Linux/ Unix.

Just learned to Dual boot Vista & Ubuntu using G Parted to create partitions.

Can you smart guys teach me how to create & restore an Image of my drive, like I used Symantec Norton Ghost/ Acronis True Image 11?

Firstly what software to use......part image, remastersys, mondo...preferably suggest what you have tried & tested on a dual boot?

Where & how to start?

How to take an exact( Cold or Hot Imaging) preferably cold......image?

How to place it on a partition or an optical media?

How to restore?

Can I create image of both Vista & Ubuntu in 1 or do I need to create 2 separate one?

Can I create an image remaining in any environment or I have to be in Ubuntu etc.

Hoping to hear from you smart people,

Thanks in advance,

Regards!

Btw Acronis True Image 11 can do it from windows....I think!

---

### Post by Yezinki on 2008-08-23
Hi there,

I did it myself..........created an image of a dual boot Vista & Ubuntu Hardy Heron 8.0.4........stored it in the Logical D NTFS of Vista partition & than restored it overwriting both over Vista & Ubuntu.........results PERFECT including boot loader etc!!

Dual Boot:

1. C: NTFS Primary 40GB Vista
2. D: NTFS Logical 20 GB 
3. /root: ext3 20 GB
4. /swap: 512 MB
5. /home: ext3 15 GB

Took 29 mins to create & the same to restore approximate.......image was split into 4 GB size to  burn on optical  media.....image size 12 GB.

Thanks alot.

Any one interested to learn PM.

Now I have perfected & now make a dual boot again with a peace of mind.........this was just a tester, experiment.

Thanks to all who helped me make a dual boot & create partitions specially Forestpixer, WRDN, mb_webguy, prshah.

Now with those 3 DVDs I can install a dual boot with all progies, special settings etc in 29 mins lol

---

