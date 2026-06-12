---
title: "Need Advice on HDD Selection"
date: 2018-11-05
forum: Hardware
---

### Post by Iggy64 on 2018-11-05
I have a Dell OptiPlex 360 desktop (roughly 10 years old).  
- The cpu is Intel Core(TM) 2 Duo E7400  2.8 GHz. 
- The Base Board (System Board / Motherboard) is Dell 0T656F. 
- The BIOS is the original Dell A02. (Upgrade to A07 is now available.)
- The HDD is Seagate BarraCuda ST3160318AS  160GB  SATA2 7200 rpm
- The SATA interface is SATA 300 (300 Mbps / 3 Gbps); i.e., SATA2


The HDD is starting to make some noises, and the SMART data show a few warnings. As I am near to upgrading my OS anyway, I figure it's time to replace the HDD.  I have a few questions:


1) Can I safely assume that a SATA3 drive is downward compatable with the SATA2 interface?  Most of the new drives appear to be SATA3.


2) Most of the new drives are also substantially larger-capacity than the existing 160 GB disk.  Is my system likely to recognize a 0.5, 1.0, or even 2.0 TB drive?  Will I have to "jump through any hoops" to utilize the entire disk?  I don't know if a BIOS upgrade would matter; but I'd rather avoid the risk of upgrading that.


Would appreciate any guidance before I choose/purchase an HDD.

---

### Post by dino99 on 2018-11-05
Old hardware are limited to 2TB due to their bios.
Indeed Sata3 is Sata2 compatible, no problem on that side. There is also pci card offering Sata3.

You can grab some hdd tests on Tomshardware for example to choose one that fit your needs..

---

### Post by Dennis N on 2018-11-05
Since you are changing the HDD, you should consider replacing it with an SSD. SATA III SSDs work with SATA II and give a huge performance boost. You will ask yourself why you didn't do this before now. Also prices are much lower recently than just a few months ago. You will need an inexpensive adapter to install one into a 3.5" drive bay.

---

### Post by Autodave on 2018-11-05
+1 with Dennis N: think about adding 2 drives: a smaller SSD (120G can be had for about $35 US) to install the OS and your programs on, and a 1 or 2 TB to use for storing music, pics, videos, etc.

---

### Post by Iggy64 on 2018-11-05
Thanks everyone!  Those are very helpful ideas.  In fact, after some thinking, they raise a few more questions:

1) Is that 2 TB limit a pretty universal rule for "old hardware"?  Is it most likely to apply to my specific case?  (The support folks at Dell were pretty noncommittal.)  Maybe there's some place to look that up, or some test to run?  

2) What would be the benefit of a SATA3 pci card?  Would it actually bump the speed from 300 to 600 Mpbs?

3) I have, in fact, been mulling over the idea of an SSD, but - with my limited knowledge - I wondered:

- Would an SSD work OK with my existing system? (BIOS, etc.)  Would the power and SATA cables fit the sockets, or would I need adapters?  Or perhaps they are built into the adapter that fits the small SSD into the 3.5" bay?

- If I put the OS on the SSD, would I best put my /home (with config files, preferences, etc.) on the SSD, with the data (Documents, Photos, music, etc.) on the extra internal HDD?

- I could probably afford to go with just the SSD, if I bump the size to around 250 GB (~$55) or 500 GB (~$80).  I don't need enormous storage space on the main drive.  My music and photos are mainly on USB HDDs, and the transfer speeds are more than adequate.  I might have a few hundred mp3s on the SSD, but I would be mainly reading them, not writing changes to them.  The music actually streams fine from the external HDDs, though.  Does any of this make sense?

- Are there any particular brands, form factors, or other design elements of SDDs that are known to offer greater reliability?

Again, I am very grateful for your input.  I know just enough to be dangerous, and not enough to be confident in this upgrade.

---

### Post by Dennis N on 2018-11-05
Definitely make a GPT partiton table when preparing any new disk and you don't have that 2 TB limitation. I used GPT even on my old 2007 Dell laptop. No more MSDOS with its primary, extended and logical partitions.

SATA power and data cables are the same for HDD and SDD -  just plug the old cables back in. SDDs are great on BIOS and UEFI computers. I am liking SSD for all purposes now.

---

### Post by Iggy64 on 2018-11-05
Thanks, again, to Dennis N. for that additional information and suggestions.  I think these are going to really help me out.  I'm definitely going to take a harder look at SSD, in combination with either an additional internal HDD or my existing external HDDs for data storage.  

Using GUID partitioning also sounds like something I should learn more about.

I really appreciate all this help!

---

### Post by Autodave on 2018-11-05
Just about everyone of my systems have an SSD (120G) and a spinner of 500G or 1 TB.  Even without the SATA 3 card, you will be amazed at the speed difference.

---

### Post by Iggy64 on 2018-11-05
Thanks Autodave --

For my further education, how do you format and partition your SSD and your HDD.  That is, what filesystem (ext4?) and what partitions of what size on each.  I think this would give me even more perspective.

---

### Post by Iggy64 on 2018-11-06
Based on the kind advice offered here in this thread, I have been investigating my options for replacing my HDD with an SSD.  After considerable study, I seem to have found that:

- If I use an SSD, I definitely want to use TRIM to preserve the life of the SSD.

- In order to use TRIM, I must operate the SATA interface in AHCI mode.

- Back in the day, the Dell web site said:  "The Dell OptiPlex 360 is the upgrade to the Optiplex 330. The Optiplex 360 can accomodate a wider range of processor types. The 360 does not have RAID or AHCI support on board."

-  In a forum, I read that "Unfortunately the 360 does not seem to have a PCI-E X1 slot, so you cannot go with a controller for your SSD and get AHCL that way."

Perhaps using SSD on this older box is not the best idea after all?

---

### Post by Autodave on 2018-11-06
Some of my spinners are EXT4, but most are NTFS so that I could swap them into any machine, if needed. As far as the partitioning on the SSDs, I just the installer do its thing and use the recommended partitioning which it will do for you. I use the entire drive for Linux.  The spinners just have one partition.  I like to keep it simple. Simple is good when you really don't need anything else.

---

### Post by Autodave on 2018-11-06
Oops: forgot about the TRIM question!  I have 2 machines that are too old for AHCI. Neither of them has had an issue so far.

Let me tell you one other thing that I do:  For my main machine (which is the one that I don't want to lose) I have a spare SSD (same make and size) that I do a complete backup to using *Redo *on it.  That way, if and when the SSD dies, it will only take me a matter of a couple minutes to pop the side off of the machine and replace the drive.

---

### Post by Dennis N on 2018-11-06
Trim is set up and run automatically on Ubuntu 18.04, so you don't need to do anything (at least I don't). Trim Info from my Ubuntu 18.04:

```
dmn@Tyana:~$ systemctl status fstrim.timer
&#9679; fstrim.timer - Discard unused blocks once a week
   Loaded: loaded (/lib/systemd/system/fstrim.timer; enabled; vendor preset: enabled)
   Active: active (waiting) since Tue 2018-11-06 10:17:47 MST; 1h 49min ago
  Trigger: Mon 2018-11-12 00:00:00 MST; 5 days left
     Docs: man:fstrim

```

So it says it will do the TRIM again in 5 days.

Added: Worried about no AHCI?
I believe most current SSD models (at least the good ones) also do their own "Garbage Collection", which I think would be working even without AHCI.

---

### Post by Iggy64 on 2018-11-06
Autodave --

Thanks for the continuing support!  I like your "keep it simple" principle.  I tend to go that direction myself, so I'll likely do something similar to your setup.  

Since you don't have AHCI available, I assume you are running your SSD without TRIM, and yet are satisfied with performance.  That is very interesting to know.

Dennis N -- 

Thanks for the heads-up on the "garbage-collection" feature in many modern SSDs.  I was quite unaware!  After your post, I did a little research and learned that this "garbage collection" is not quite as comprehensive as what TRIM can do, and that TRIM actually makes the garbage collection more effective.  The consensus, though, is that garbage collection without TRIM is nevertheless pretty good, and will serve you well even without TRIM.  I wonder if Autodave's SSD has the garbage collection feature.

I'm going to be doing some more research to try to determine which SSDs actually have this feature, so I can choose one of those.

Again, thanks to both of you for helping me with this.  It has really sped up the process for me!

---

