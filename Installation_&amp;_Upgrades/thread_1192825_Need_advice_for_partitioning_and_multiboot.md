---
title: "Need advice for partitioning and multiboot"
date: 2009-06-20
forum: Installation &amp; Upgrades
---

### Post by Hilko on 2009-06-20
Hi, I am kind of new to installing linux and could use some help or advice. I'm about to reinstall my laptop and wish to install the following operating systems;

Windows Vista
Ubuntu (latest stable version)
Backtrack 3
Ubuntu Studio

Furthermore I wish to have a seperate /home partition and have some flexability to maybe add another OS later.
Now I have the following questions:

1) Can I use the same /home partition for Ubuntu, UbuntuStudio and Backtrack ? Or do they all need their own partition ?

2) Can the linux OS all share the same swap partition ?

3) If multiple OS's share the same /home, do I need to use different usernames or exactly the same username ?

4) Is it a good idea to have a seperate boot partition ? and why ?

5) Which filesystems would you recommend ?

6) Wich partitions should be primary and secondary ? what does it matter ?

7) Anything else I should think of ? (I've made backups)

Any awnser to some or all of these questions will be very much appreciated. It would be most helpful if some experienced user could just sketch a recommended partition table for this setup.
Many thanks !

---

### Post by ajgreeny on 2009-06-20
> **Hilko said:**
> Hi, I am kind of new to installing linux and could use some help or advice. I'm about to reinstall my laptop and wish to install the following operating systems;

Windows Vista
Ubuntu (latest stable version)
Backtrack 3
Ubuntu Studio

Furthermore I wish to have a seperate /home partition and have some flexability to maybe add another OS later.
Now I have the following questions:

1) Can I use the same /home partition for Ubuntu, UbuntuStudio and Backtrack ? Or do they all need their own partition ?

2) Can the linux OS all share the same swap partition ?

3) If multiple OS's share the same /home, do I need to use different usernames or exactly the same username ?

4) Is it a good idea to have a seperate boot partition ? and why ?

5) Which filesystems would you recommend ?

6) Wich partitions should be primary and secondary ? what does it matter ?

7) Anything else I should think of ? (I've made backups)

Any awnser to some or all of these questions will be very much appreciated. It would be most helpful if some experienced user could just sketch a recommended partition table for this setup.
Many thanks !
1   You probably could for Ubuntu and UbuntuStudio if they are both 9.04 but not Backtrack which is based on slax.  Even with the two Ubuntus, it may cause some configuration problems so is probably safest to keep separate /home folders/partitions, or as you suggest in No3, have a different username.  You can also have  home folders just for the configuration and other hidden folders and files for each, and have a common /data partition.

2   Yes, no problem with the swap being common to all.

3   See answer to 1

4   Not really needed these days, in my opinion.

5   I personally stick with ext3 and see no good reason to change from that.

6   It does not matter at all for linux distros.  Only windows gets upset and will not boot on an extended partition.

7   As long as you have backups and can avoid touching your windows partition there should be no major difficulties as far as I can see.

---

### Post by starcraft.man on 2009-06-20
I think ajgreeny did an admirable job answering all your questions you listed. I'd only add my 2 cents of a quick partition sketch of how I'd do it.

*- Primary*
**-> Extended space partition**

Drive X
[I]- Windows
- Backtrack 3
- (can insert here another OS later, remember to regenerate GRUB or edit manually after)[/I]
[B]-> /Home
-> Ubuntu
-> Ubuntu Studio
-> Swap
[/B]
I'd also like to make sure you know that there isn't anything special about Ubuntu studio to my knowledge. It is just Ubuntu with a whole lot of extra AV programs preinstalled (and configured some I believe), they can be gotten from the repos once all portions are enabled on a standard install. Just making sure you know, it's not like a whole different OS, just a custom build.

---

### Post by Hilko on 2009-06-20
Thank you very much for the quick replies. It's fantastic to get a response so soon.
> 5 I personally stick with ext3 and see no good reason to change from that.
Isn't Ext4 better or faster ? or it doesn't matter ?

Something I forgot to ask; Is the order of the partitions important ? I've heard that windows should be in the first. But what about swap, should that be at the end or second ?
And if i leave some diskspace unpartitioned, (to add a new OS later), does it have to be at the end or can it be in the middle ? Or if i wish to delete say, UbuntuStudio, can I merge that partition to /home ?

Thanks !

---

### Post by starcraft.man on 2009-06-20
> **Hilko said:**
> Thank you very much for the quick replies. It's fantastic to get a response so soon.

Isn't Ext4 better or faster ? or it doesn't matter ?



Yes, it's faster in the benchmarks but at the same time from what I understand they had to cut back on some of the fail safe reliability. If I were to put this in blunt terms, if one were storing life or death data on it, I would use EXT3 or NTFS. Assuming you have none of that, I am told that EXT4 seems to run fine since some later updates than when I tried it. I can't council you further than that, I think most of the kinks are out and besides which, all your critical data should be backed up. I remember the wise words of a tech guy: Data doesn't exist unless it's in at least two places... or some such.

> Something I forgot to ask; Is the order of the partitions important ? 

No. The order of the partitions is irrelevant (i.e. whether ubuntu studio or swap is first in extended space in my example makes no difference). The only thing that is important is that Windows should be **Primary**. Linux and Slax are much better at being anywhere on a drive. 
> 
I've heard that windows should be in the first. But what about swap, should that be at the end or second ?

Please see the exemplar partitioning that I listed in my previous post. That is a good division. If you really must know the specifics, I direct you to [the gparted documentation]("http://gparted.sourceforge.net/documentation.php"). See the english html sections starting with the basics. Very good stuff. Make sure you understand difference between primary and extended after reading it, then my list will make sense.

> And if i leave some diskspace unpartitioned, (to add a new OS later), does it have to be at the end or can it be in the middle ? Or if i wish to delete say, UbuntuStudio, can I merge that partition to /home ?
Again, a question best handled by [gparted documentation.]("http://gparted.sourceforge.net/larry/tips/gfs.htm") The basic gist of it is that no, you can't just use free space and merge it with any other partition. To do such an action, the space must be contiguous with the partition you want to merge into or resize. Basically, they need to be side by side, read the gparted notes and ask questions if you don't understand. And for the love of all things Linux DON'T make permanent changes to your partitioning until your sure, you don't cancel in the middle of such actions.  In any case, existing partitions can be resized to make more free space (long as the partition in question has free space), and that space then moved into and out of extended/primary partitions. It just takes time.

I think that's all your questions, feel free to ask more :).

---

### Post by Hilko on 2009-06-20
Thank you very much starcraft.men for your complete and clear awnsers. I am reading the gparted documentation now. It's a valuable reference, as I want to know and understand what i'm doing, before i do it.
Tomorrow i'll repartition my drive.
Thank you very much !

---

### Post by starcraft.man on 2009-06-20
> **Hilko said:**
> Thank you very much starcraft.men for your complete and clear awnsers. I am reading the gparted documentation now. It's a valuable reference, as I want to know and understand what i'm doing, before i do it.
Tomorrow i'll repartition my drive.
Thank you very much !

No problem, your quite welcome. If you got any questions after reading the documentation I'll be around tomorrow some time. En Taro Adun!

---

### Post by ZootHornRollo on 2009-06-23
this is a great thread.

Thank you very much to both the OP and the informative answers from the contributors.

it has answered many question for me regarding an installation of uStudio.

---

