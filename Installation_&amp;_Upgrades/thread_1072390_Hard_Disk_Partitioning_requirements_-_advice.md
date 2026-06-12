---
title: "Hard Disk Partitioning requirements - advice"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by npinn001 on 2009-02-17
Hi,

In  a wierd circle i have tried ubuntu, left for fedora, and now am back to Ubuntu in a month. completely new to linux, and i previously installed linux on one partition.

Now i have about 250gb hard drive, 3GB RAM and i want to install ubuntu properly.

I am planning a file system as:
/ (root drive)
/Home (all my home directories and files)
Swap

What should i be looking at to have a running flexible system. I would like to have enough space on / to upgrade to future versions without running out, but dont want to waste 50gb on this partition, so what would be good? Also i will be adding GNUCASH, mp3 support etc from the out of box install. How much for swap? Any advice would be great.

---

### Post by dox_drum on 2009-02-17
I'd do something like

[LIST]
[*]SWAP: 6-8 GB (approx 2.5 times your RAM)
[*]/: about 15GB
[*]/home: about 200GB
[*]/databk: the rest of free space (for backing up the really important things)
[/LIST]

Best regards.

[CENTER]Enjoy![/CENTER]

---

### Post by npinn001 on 2009-02-17
Thanks for the fastest response i have ever got off any forum! Seriously, thubs up big time. I never considered a /DataBK file, i will look into that - Based on your reccomendation, could you also help me with a couple of bits:

1) Does it matter the order they are put on the hard drive, ie does swap get done last or first, does / need to come before /home?
2) Does it matter about file types, i was going to use primary as file type for all except swap, is this right?

SWAP: 6-8 GB (approx 2.5 times your RAM) 
/: about 15GB 
/home: about 200GB 
/databk: the rest of free space (for backing up the really important things)

---

### Post by dox_drum on 2009-02-17
> **npinn001 said:**
> Thanks for the fastest response 

You're welcome!

> **npinn001 said:**
> 1) Does it matter the order they are put on the hard drive, ie does swap get done last or first, does / need to come before /home?

As far as I know, It doesn't matter. 

> **npinn001 said:**
> 2) Does it matter about file types, i was going to use primary as file type for all except swap, is this right?

I use primary ext3 for everything but swap, and they work well. But seriusly, I do not know much on the subject.

I saw a nice post about partitioning a HD... everything explained. If I find it again, I'll let you know.

[CENTER]Enjoy![/CENTER]

---

### Post by npinn001 on 2009-02-17
Cheers again, i will do a google on file types.

---

### Post by Forlornity on 2009-02-17
Personally, I have about 20-30 GB for / then mount the rest of my linux dedicated as /home.

I don't think it's all that necessary to have much swap with that much RAM, 3GB should be enough, back when we had 256 megs tops it was sensible to have a lot more swap space, but with 3GB you're unlikely to need that much.

Also as regards filesystems, generally ext3 is a good choice, unless you're on an SSD, in which case it will shorten the lifetime of your drive rather a lot :P
If you ARE on an SSD, ext2 is a good choice.

Regards, Forlornity

---

### Post by dox_drum on 2009-02-17
> **Forlornity said:**
> Personally, I have about 20-30 GB for / then mount the rest of my linux dedicated as /home.

I'd do the same if I expect to install a huge amount of programs, but otherwise 15GB is a fair size. 

Additionally an extra partition to keeping your personals could be useful. The size is up to you... How much important files do you have? I've just like 1GB.

> **Forlornity said:**
> I don't think it's all that necessary to have much swap with that much RAM, 3GB should be enough, back when we had 256 megs tops it was sensible to have a lot more swap space, but with 3GB you're unlikely to need that much.

It is true that 3GB is quite a RAM memory, but having enough swap allows your computer to run with ease and help in case of invernation... of keeping your files when your battery runs out of charge. 

> **Forlornity said:**
> Also as regards filesystems, generally ext3 is a good choice, unless you're on an SSD, in which case it will shorten the lifetime of your drive rather a lot :P
If you ARE on an SSD, ext2 is a good choice.


Thank you very much for your advise! I didn't know such a thing.

Have you any idea about the behaviour of the coming ext4 with SSD?

[CENTER]Cheers[/CENTER]

---

### Post by npinn001 on 2009-02-17
Cheers forlornity and Dox_drum, im really chuffed with the speed of responses on here, another good reason to move to ubuntu. Im going to do it tonight and let you know how i get on. Cheers

---

### Post by npinn001 on 2009-02-17
Additionally an extra partition to keeping your personals could be useful. The size is up to you... How much important files do you have? I've just like 1GB.

How do you mean.....i was going to keep all documents and music in /Home, so are you saying it might be worht me looking at setting up a new one for personal items?

---

### Post by dox_drum on 2009-02-17
> **npinn001 said:**
> How do you mean.....i was going to keep all documents and music in /Home, so are you saying it might be worht me looking at setting up a new one for personal items?

Yes, I strongly suggest to have an extra partition.

I'm a grad. student, and I keep an additional copy of my work in a /data/ partition, as I said, is just extra security. You may skip it if you prefer, and bkp your file burning a CD, or in a pendrive.

---

### Post by vanadium on 2009-02-17
Removable USB drives are cheap nowadays and a much more secure way to backup your data.If your hard drive fails, all your partitions, including your backup, will be lost.

Keep it simple for a desktop system. With a large drive, a root (10-15 GB), a home partition and a swap are just fine. For smaller disks (< 80 GB), I would not even bother for a separate home.

---

### Post by redroad55 on 2009-02-17
A good argument for a /home  partition is that if you decide in a couple of years the new kernel has features that you can't live without .. You can upgrade without loosing your files and settings .. Also on any given hard drive you can only have 4 primary partitions .. so if you partition that way expansion is very limited .. So what I do is make the /home partition logical rather than primary and position it as last partition on the drive so I can expand it to the right > new drive if needed ...The /home partition is really the only partition that will grow significantly with time..Best to you

---

### Post by az on 2009-02-17
I wouldn't use or recommend a separate home for any drive.  As has been said, removable drives are very cheap and a lot easier to use than playing with partitions.

The default install doesn't create a separate home partition.  I would stick with that.

---

### Post by npinn001 on 2009-02-18
cheers for all the help, dowloaded live cd going to install tonight.

---

