---
title: "Please Help Me Install Dual OS"
date: 2006-01-14
forum: Installation &amp; Upgrades
---

### Post by amwil1024 on 2006-01-14
I want to install Ubuntu without losing my current MS-OS,

My current system information,
Win98SE, HD=Available space is 9958MB (Fat32), Pentium III with 511MB RAM.

I see from reading the Ubuntu cover that I must use expert installation mode to do a dual OS set up.

First, I'm not an expert, will someone walk me thru dual os install so that I do not accidentally erase my current OS?

Mike "Piedmont"

---

### Post by jsmidt on 2006-01-14
To do a dual boot you need to install on different partitions.

The easiest way to do this is to set op you other operating system on a partition of you hard drive.  Then using ubuntu's install CD you want to make the partition you don't want to use for other OS's besides Ubuntu free space with their partitioner.  Once it is free space select from the partition menu guided partitioning.  Select use largest amount of continuos free space.  It will partition the free space for you.  Then say keep the changes.

*Don't turn your other OS's partition into free space!*  ONly the partition you want to use for Ubuntu!

---

### Post by Herman on 2006-01-14
[http://users.bigpond.net.au/hermanzone/p2.htm]("http://users.bigpond.net.au/hermanzone/p2.htm")
Try having a look at the above link and see if that helps you. You shouldn't try the 'expert' install mode unless you have a special reason to need it, and you know what you are doing.
The 'default' install is really the best, in spite of its humble name.
Good luck with it, :D (Herman)

---

### Post by amwil1024 on 2006-01-14
Yes, I understand what you suggested, but what I need is, after I restart my pc with the Ubuntu Install CD in the CD-Rom, and after I go to Ubuntu Expert Installation Mode, from this point I would be most comfortable with advice on what to select as I go through the "Manual Partion" section. That is, I assume that I would select manual partion as the other two choices both mention erasing the entire hardrive.

---

### Post by amwil1024 on 2006-01-14
Herman,

As I understand it, quoting from the Ubuntu cover, "the default installation will erase all existing software and data from your computer", and that isn't what I want to happen. I want to install Ubuntu right along with my existing OS. The cover states that one must go through expert install mode in order to do a dual os set up.

---

### Post by amwil1024 on 2006-01-14
[QUOTE=Herman][http://users.bigpond.net.au/hermanzone/p2.htm]("http://users.bigpond.net.au/hermanzone/p2.htm")
Try having a look at the above link and see if that helps you. You shouldn't try the 'expert' install mode unless you have a special reason to need it, and you know what you are doing.
The 'default' install is really the best, in spite of its humble name.
Good luck with it, :D (Herman)[/QUOTE]

I went to your suggested page and it does indeed suggest that I can set up dual os without using expert mode, I will carefully read through you instructions and give it a go. The part about setting up the percent partion is confusing as you wrote, I did assume it was asking for the size of the parttion for Ubuntu, but that in fact it is assiging a partion size for my existing os/system.

Mike "Piedmont"

---

### Post by amwil1024 on 2006-01-14
[QUOTE=Herman][http://users.bigpond.net.au/hermanzone/p2.htm]("http://users.bigpond.net.au/hermanzone/p2.htm")
Try having a look at the above link and see if that helps you. You shouldn't try the 'expert' install mode unless you have a special reason to need it, and you know what you are doing.
The 'default' install is really the best, in spite of its humble name.
Good luck with it, :D (Herman)[/QUOTE]

To Herman or Anyone;

I clicked "enter" for default install at "boot:".
No such thing as "Resize IDE1 master, partition #1 (hda1) and use free space"!? When partition HD stage came up. Now what!?

My Ubuntu version is 5.10

Mike "Piedmont"

---

### Post by Herman on 2006-01-14
>  I clicked "enter" for default install at "boot:".
No such thing as "Resize IDE1 master, partition #1 (hda1) and use free space"!? When partition HD stage came up. Now what!? Wow! Really? That's odd. Have you got 'manually edit partition table then?
If you do, you can use that, it does the same thing essentially. 
After selecting that and pressing 'enter', you can do the same as illustrated in 8 to 14 ntfs, in the [Ubuntu+ntfs]("http://users.bigpond.net.au/hermanzone/p3.htm") example install (but substitute your own sizes for the partition of course). Then at 15 ntfs illustration, just choose 'automatically partition the free space'.

The "Resize IDE1 master, partition #1 (hda1) and use free space" is a nice shortcut, but the way to do it as described in the NTFS install is just the more traditional way of doing the same thing, it's just a few steps longer. So detour through those steps (8 to 15 ntfs), and then return to your fat32 install. I think step 15 ntfs will bring you bcak to step 10 fat32 when you return back to your right install page again. 
I hope I've made that simple enough to understand, let me know if you are still indoubt, I'll be here, :D (Herman)

---

### Post by amwil1024 on 2006-01-14
[QUOTE=Herman]Wow! Really? That's odd. Have you got 'manually edit partition table then?
If you do, you can use that, it does the same thing essentially. 
After selecting that and pressing 'enter', you can do the same as illustrated in snip
I hope I've made that simple enough to understand, let me know if you are still indoubt, I'll be here, :D (Herman)[/QUOTE]

Thanks Herman,

I'm running out of time for today and will review this new information, I glanced over it and was over whelmed a bit. Perhaps if I give the following info you could help me with the entries?

My HD is 12.76 GB, I thought that I would make my partition for my old OS at 8GB and leave the balance for Ubuntu use. You have been very helpful and friendly and want you to know that I appreciate your efforts to get me going!

Mike "Piedmont"

---

### Post by Herman on 2006-01-14
Sure, Mike, I'm pleased to be able to help. I'll be lurking around. My working hours are extremely eratic and unpredictable, that's one of the reasons I decided to make the website so as not to leave people stuck if I can't be here. Chances are I'll be around tho', sooner or later, next time you post.  :D (Herman).

---

### Post by amwil1024 on 2006-01-14
Herman,

I just tried it again and this time it came up! "Resize IDE1 master, partition #1 (hda1) and use free space" So I tried it and it came up with a value of 8.5GB so I tried that as it was close to what I wanted for the old OS, bu it came back that there wasn't enough free space for ubuntu, How much will ubuntu need? how much can I leave for my old OS?

Mike "Piedmont"

---

### Post by Herman on 2006-01-14
Ubuntu should only need 1.8 GB at the extreme minimum, and I have installed it on 3.0 GB plenty of times, with a swap partition of around two or three times my ram, or 1.0 GB, whichever comes first. In your case it should automatically figure out how much swap you need. 
That adds up to about 4.0 GB, total, that should be all you need for a working system as long as you don't need to save a lot of large files like movies or music or anything like that. You'll have room for some e-mail and text files. It should be okay.
You said you have 12.7 GB and Windows was going to be 8.5. That would leave 4.2 for Ubuntu, that should have been okay, just try once more if you want, and if it doesn't work maybe reduce Window's size to 8.0 as originally planned and see if that works, you must be close! :D (Herman).

---

### Post by amwil1024 on 2006-01-14
Hi Herman

I went as low as 4 GB (don't want to go that low) for old os resizing and still get not enough room. The install shows 12.. GB or my HD, what can be going on?

---

### Post by Herman on 2006-01-14
I don't know, that's really weird...have you defragged your old operating system?, and checked the amount of available disk space in drive C?
(Start, My computer, drive C, properties if I remember correctly.... it's been a long time...) :D (Herman)

---

