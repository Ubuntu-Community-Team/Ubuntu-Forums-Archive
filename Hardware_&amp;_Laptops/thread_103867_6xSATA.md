---
title: "6xSATA"
date: 2005-12-14
forum: Hardware &amp; Laptops
---

### Post by adduds on 2005-12-14
Hey all!

Hope everyone is well everywhere. Probably not the best post, but I love this community and try to help people as much as I can and now I need some help. I just had a couple questions that I couldn't find answers to. I own a ASUS K8N-E Deluxe mobo and some specs are as follows:

3x184pin DIMM Sockets support max 3GB 

1. So can i put 2 512MB sticks and one 1 GB stick? I'm pretty sure i can right?

Dual RAID 6xSATA

2. So does this mean I can have 6 hard drives?
3. What is Dual RAID?

In my user manual it says:

SATA1 and SATA2 and then SATA_RAID1 SATA_RAID2 SATA_RAID3 SATA_RAID4

4. what's the difference between my sata1 and sata2 and the rest?

5. What's the difference between RAID0(stripped), RAID1(mirrored)? (I have some idea but a nice clarification would be nice)

I ask because I have a 200GB Seagate SATA and I'm getting another 250GB Seagate SATA for christmas. Which I plan on making into a dual boot system

---

### Post by Sutekh on 2005-12-14
> **adduds]Hey all!

Hope everyone is well everywhere. Probably not the best post, but I love this community and try to help people as much as I can and now I need some help. I just had a couple questions that I couldn't find answers to. I own a ASUS K8N-E Deluxe mobo and some specs are as follows:

3x184pin DIMM Sockets support max 3GB 

1. So can i put 2 512MB sticks and one 1 GB stick? I'm pretty sure i can right?
[/QUOTE]
Sounds reasonable to me, but you'd want them to be all the same speed, DDR400 or whatever, because I'm pretty sure they'll run at the speed of the slowest one.  Your manual should have all the possible memory configuarions and speeds.

[QUOTE=adduds]
Dual RAID 6xSATA

2. So does this mean I can have 6 hard drives?
[/QUOTE]
Yes, 6 SATA Drives

[QUOTE=adduds]
3. What is Dual RAID?

In my user manual it says:

SATA1 and SATA2 and then SATA_RAID1 SATA_RAID2 SATA_RAID3 SATA_RAID4
[/QUOTE]
There are two chipsets, and two SATA controllers on your motherboard...

[QUOTE=adduds]
4. what's the difference between my sata1 and sata2 and the rest?
[/QUOTE]
The first two are the native SATA ports, as in they are the NVIDIA chipset SATA ports.  The others are the second chipset's (Silicon Image SIL3114) SATA ports.

[QUOTE=adduds]
5. What's the difference between RAID0(stripped), RAID1(mirrored)? (I have some idea but a nice clarification would be nice)
[/QUOTE]
RAID0 (striped, not stripped haha) means that data is broken into blocks and written across the drives in the RAID0 configuration.  This has good performance when each drive is on a different controller.  ie SATA1 and SATA_RAID1.  RAID0 is not good, because if one drive fails, ALL data is gone.  

RAID1(mirrored) means that data on one SATA drive is "mirrored" on the other drive in the RAID1 configuration.  They only mirror in pairs, so 3 SATAs in RAID1 is silly.  Basically if one drive goes down the other will have a copy of it.  Data is written as one oepration to both discs, but can be read from any one particular disc.

There are other RAID configurations, if you are interested to read about here said:**
> RAID Tutorial[/URL] or here; [Wikipedia - RAID]("http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks")

[QUOTE=adduds]
I ask because I have a 200GB Seagate SATA and I'm getting another 250GB Seagate SATA for christmas. Which I plan on making into a dual boot system
If you are going to do a dual boot system, I'd put one OS on each disc and forget RAID.  Other people might be able to suggest a good use for your hard drives, but unless you are really into having redudant data, a must for some applications, I wouldn't worry.

---

### Post by adduds on 2005-12-15
Thank you very much for your well informed, thorough response. I was very much so planning on just having an OS on each HD, so thanks again.

Say, theoretically, I purchased a third HD.

1. Would I then have to go RAID?

---

### Post by Sutekh on 2005-12-15
If you get a third drive, then yes you could go RAID.  The real answer is, what do you want to do?  You could use the third drive to mirror one of the others.  Plus there are other RAID configurations you could consider.  It just depends on what you want and what you need.

Just for interest, I have 3 SATA discs.  One with WinXP, one Ubuntu and one a shared disc.  The total size is more than I could ever need, so I just use the third disc to backup the most important things from Windows and Ubuntu.  I think that for me its more appropriate to backup my personal data/configs rather than the whole disc, if say I used the third disc to mirror Ubuntu ala RAID0.  

As for an OS on each disc, I found that terribly easy to setup.  
Good Luck! :p

---

### Post by psusi on 2005-12-15
I have an Asus K8V Deluxe motherboard, which I think is almost the same as yours.  

I have two 36 gig 10,000 rpm WD raptor drives in a raid0, and I dual boot winxp ( though I have not used it in a long time ) and ubuntu ( both breezy and dapper ).  

I sugest that the second drive you get be the exact same model as the first, and you configure them like I do, because it is nice and fast.  

You should also read [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto).

---

### Post by adduds on 2005-12-15
> I sugest that the second drive you get be the exact same model as the first

why?

---

### Post by joshuapurcell on 2005-12-16
[QUOTE=adduds]why?[/QUOTE]
The only reason for keeping the drives identical if to make sure both are capable of the same speed. I'm sure you would be able to run different types of hard drives in a RAID array, but you would very likely lose any performance benefit from running just the faster hard drive. You would gain more space though, and possibly RAID benefits like mirroring, striping, etc. (depending on how you set it up).

I have an ASUS K8V Deluxe, and I actually had an ASUS K8N-E Deluxe installed for about a week several days ago while I was troubleshooting hardware problems (none of which were related to either motherboard as it turns out). Both motherboards are very nice. The only minor complaint is that I would rather have one good RAID controller rather than two for simplicity and faster boot times, but that's a small complaint... I just try not to restart the computer very often :D.

You may want to set up your drives as logical volumes within a volume group, so you can change partition sizes, as well as move partitions (and physical drives) around as needed:
[http://www.tldp.org/HOWTO/LVM-HOWTO/](http://www.tldp.org/HOWTO/LVM-HOWTO/)

Here's some info on RAID and various RAID configurations:
[http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks)

I like to use RAID 0, since it make accessing the hard drives much faster by splitting the partitions across multiple physical drives (but if one drive goes out you lose everything... I'm OK with that but others may not be).

---

### Post by Sutekh on 2005-12-16
[QUOTE=joshuapurcell]The only reason for keeping the drives identical if to make sure both are capable of the same speed. I'm sure you would be able to run different types of hard drives in a RAID array, but you would very likely lose any performance benefit from running just the faster hard drive. You would gain more space though, and possibly RAID benefits like mirroring, striping, etc. (depending on how you set it up).[/QUOTE]

More than just the same speed, the same size, otherwise there will be wasted space.  RAID0 (striping) discs of different sizes, uses the smaller size as a limit.  So striping your (**adduds**) 200GB and 250GB would amount to a total of 400GB NOT 450GB, which is what you'd think.

Same with RAID1 (mirroring), the 250GB would mirror the 200GB, and the remaining 50GB would be doing nothing.

---

