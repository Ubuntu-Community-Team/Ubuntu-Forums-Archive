---
title: "merging disk parts together"
date: 2009-08-11
forum: Hardware
---

### Post by cimbaeth on 2009-08-11
Hi,

well I have on my 250 Gb HDD these parts:

```
/dev/sda1: UUID="E234C7E334C7B935" TYPE="ntfs" 
/dev/sda2: UUID="2C88743C8874071C" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="6123740e-0421-4208-8a1a-07863a9f6f92" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="32364fe0-d0d4-422d-afc5-91f9351ec61e" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="5c37a610-896e-40c7-9bc6-77a3199bada1" 
/dev/sda8: TYPE="swap" UUID="0f7758b2-51e0-448c-a062-e2722412b4d9" 

```

in sizes:
sda1:73,42 Gb - Vista -> wanna delete completely
sda2:8,20  Gb - HP_Recovery - delete probably
sda3:151,26Gb
[INDENT][LIST]
[*]sda5:2,86  Gb - boot
[*]sda6:136,81Gb - /
[*]sda7:5,80  Gb - swap
[*]sda8:7,81  Mb - another swap - for nothing
[*]and 5,78 Gb free space unassigned
[/LIST]
[/INDENT]

thinking of a bit remaking it.

I'd like to make it faster and simplier.
Something like this:
[LIST]
[*]should keep boot so that can remain
[*]like trying new distros, so I can have some side part with size about 30GB
[*]is it okay keep all data on one partition?
[*]or better split disk into 2 partitions about 100GB and rest?
[/LIST]
what I want is some secure advise on how to do it :) thanks

---

### Post by xenonR on 2009-08-11
Hi.

Wow, 2.86 GB boot...

First, there is no perfect setup it depends on your personal flavour. And simple well, simple to move to another Linux? Simple to manage? Simple to what? ;)

But **i** would do something like:
sda1 /boot 64MB (more then enough for me)
sda2 / 218GB
sda3 "testing" 30GB ( ~15GB for distro, rest to test out stuff)
sda4 swap 1.5GB (basicly Ram*3, if you have Ram >1GB i would go with Ram*2 or just the Ram size)

You could make optinaly /home a own partition to keep your user data in place in case of a new insatllation.

Basicly it's fine to keep all the data on one partition since it's one physical disk.
But as mentioned you can use the advantage of mounting /home to an seperate partition.

Btw. you can also take a look at Swap-Files instead of Swap-Partitions just to be flexible ;)

-xenonR

[I]English not my native, so don't argue! :P

PS: [/I]
I think the HP_Recovery is only practicable for Windows restores. But i may be prooved wrong.

---

### Post by ZaHACKieL on 2009-08-11
Hi cimbaeth. So, you want to get rid of Windows for good? 
I have a dual boot Win/Ubuntu laptop in a 320HD. I use windows maybe twice a year but I left it there because maybe one day I will need it.
So, I use a small partition for Windows, a shared NTFS big partition for my personal data (in case I have to access that data from Win) and the rest for Ubuntu and swap.

So, if you only want Linux in your machine I would say that you should have a big partition for your Ubuntu. The home directory is fine for your personal data. And leave an unallocated space (the size you think is enough, like the 30GB you said) so you can install a new distro there and you can share the home directory.

That's just my personal opinion, I would like to hear other people's suggestions. What do you think? sounds nice?

ZL

---

### Post by cimbaeth on 2009-08-11
2 ZaHACKieL : Well, the only reason why I sometimes use W is my Garmin watch while I am having training database on it and haven't found it working with WINE yet :-(

2 xenonR : With HP_Recovery you are right, however I never used it :D so I don't know whats in O:-) . To the /boot partition - 64MB isn't enough for me, mine has nowadays 180MB at least(maybe I should compile lighter core).

So I should make it like this? Big partition with data(music, movies, programs etc.) for mounting to any distro I like  - 200GB. Second partition for main distro - I remain on Ubuntu I think - is 10GB enough? Third partition - testing one - 30GB.


My notebook has inside : Intel Core2 Duo T7250 2,0GHZ, 2GB RAM, 250 GB HDD, 256 MB 8400 GS Nvidia.

P.S. Question how properly I should do it will come in next round :)

---

### Post by ZaHACKieL on 2009-08-11
Mmm...so...if you still want to have Win in your machine, then keep a partition for that. First install windows and then do the rest. If you are going to use Win just for that specific software maybe you can have the personal files related to that software in a folder in the same Win partition to avoid creating another NTFS partition

---

