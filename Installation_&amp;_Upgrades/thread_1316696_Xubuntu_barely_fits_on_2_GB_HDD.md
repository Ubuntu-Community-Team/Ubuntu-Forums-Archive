---
title: "Xubuntu barely fits on 2 GB HDD"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by rfurgy on 2009-11-06
This post is mainly to do with the amount of space needed on the hard drive for the install and updates of Xubuntu 9.10

I recently installed Xubuntu 9.10 on a bare minimum desktop PC that has a 2.1 GB hard drive.

First thing I ran into was during the install. The partitioner stops and warns me that the main partition isn't large enough. The '/' partition needed to be 1951890944 (1951 MB) but the default set up left me a couple MB short so I needed to manually set the partitions. I set '/' to 1960 and the rest to the 'Swap' partition. With this, Xubuntu then installs fine.

Second thing that came up was during the update process. There isn't enough space on the hard drive to do the updates. I was able to get all the Security updates installed but that was it. I found that by removing the gnome-games packages with synaptic then gives me enough space to apply all updates, Security and Recommended.

Wanted to let this be know because Xubuntu is stated as needing 1.5 GB (1500 MB) on hard drive. I suspect this is no longer accurate. I had about 25 MB left open on my primary partition after install. It did fit in the 1.96 GB (1960 MB) partition but this doesn't take space needed for updates into account.

On a side note, I ended up filling the partition to the max and then Xubuntu could no longer function properly. I couldn't even start anything to be able to remove stuff to free up space again.

Please help this post find its way to those who should really know about this. Thank you.

---

### Post by TenPlus1 on 2009-11-06
If you have more than 512mb memory you can remove the swap parition and that'll leave you with around 600mb of space to do your updates with...  That's how I work Xubuntu on my virtualbox install...  works fine...  remove software from the install you dont use also...

---

### Post by Mighty_Joe on 2009-11-06
Bug reports go in [Launchpad]("https://launchpad.net/").  The forums are for the user community.

---

### Post by rfurgy on 2010-02-28
Was thinking this wasn't exactly a bug, just misinformation. Should I post it in the Xubuntu Forum? That is if there is one.

---

### Post by Mighty_Joe on 2010-03-01
My point is that the people who would fix such a problem do not frequent this forum.  Launchpad is probably the most direct way to draw attention to it.

---

### Post by presence1960 on 2010-03-01
2.1 GB? you got to be kidding. Even if you can get it on there and update once, when more updates come down the pike you will be out of room again. get a bigger HDD is the only practical solution.

---

### Post by Skaperen on 2010-03-01
> **presence1960 said:**
> 2.1 GB? you got to be kidding. Even if you can get it on there and update once, when more updates come down the pike you will be out of room again. get a bigger HDD is the only practical solution.Or maybe a smaller distribution.  How about getting rid of X and graphics altogether ... ttybuntu anyone? :D

---

### Post by PhilGil on 2010-03-01
You might want to consider a lighter distro like Puppy Linux or DSL.  If you want a Ubuntu derivative (and don't mind "computing on the edge") Lubuntu 10.4 is coming along quite nicely and has a smaller footprint than Ubuntu, Kubuntu or Xubuntu.

---

### Post by presence1960 on 2010-03-01
> **PhilGil said:**
> You might want to consider a lighter distro like Puppy Linux or DSL.  If you want a Ubuntu derivative (and don't mind "computing on the edge") Lubuntu 10.4 is coming along quite nicely and has a smaller footprint than Ubuntu, Kubuntu or Xubuntu.

Even lucid will occupy close to 90% of the disk. When a hard disk gets over 90% performance really suffers. Face the facts- 2.1 GB is not an ideal disk to have nowadays and that is putting it nicely. I would get a bigger disk or scrap the whole thing.

Either way the OP is really pushing his luck. See here for minimum (bare) and recommended system requirements for xubuntu: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by rfurgy on 2010-03-01
It was purely for trial. LOL :lol:

I was going by the specified size needed and found out it took more than was listed at the time. Besides, the process put the drive through stress and revealed to be bad. Only lasted about a week. LOL

---

### Post by efflandt on 2010-03-02
When I did a regular install to 4 GB USB, I think Ubuntu after updates and adding video applications/codecs took up about 2.7 GB.  Bootable iso takes up less space and can run on less that 2 GB including persistent data, but it boots a compressed filesystem (squashfs) that is difficult to modify or update unless you know what you are doing.

A certain amount of disk space is reserved for root, so users to not totally choke the system.  That can be adjusted with **tunefs**.  But 2.1 GB is still too thin for a "full" Ubuntu installation.

---

### Post by rfurgy on 2010-03-02
> **efflandt said:**
> A certain amount of disk space is reserved for root, so users to not totally choke the system.  That can be adjusted with **tunefs**.  But 2.1 GB is still too thin for a "full" Ubuntu installation.
I would agree with that. I could see using less space if I was to install to a USB with casper. I still prefer the full install though, much more that can be done with a system that way.

I still chuckle when I think about having a 2 GB hard drive and trying to use it. But hey, I wanted to find out if it could be used for anything and if it was good or not.

I also just pitched two 4 GB hard drives that died while using them. Double the room and can be used for Xubuntu easily, but they are old drives and need to be put to the test before I'll actually use them in a PC I give away. Even if they end up as a storage drive, last thing I need is for a hard drive to crash on a PC I've gifted.

LOL, my USB jump drive has 8 GB, kind of amazing how far computers have come.

---

