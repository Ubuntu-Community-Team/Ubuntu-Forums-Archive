---
title: "4TB RAID-0: can only access 1.64TiB"
date: 2011-07-02
forum: Hardware
---

### Post by Bitage on 2011-07-02
[SIZE=2]**Hardware used**
[/SIZE] [SIZE=2][I]- MSI 790X-G45 motherboard
- old drives: 2x Samsung EcoGreen F2 HD502HI, 500GB
- new drives: 2x Hitachi Deskstar 5K3000, 2TB
- using the onboard AMD RAID capability
- using the Ubuntu 11.04 live CD
[/I] 
Since my current RAID-0 config of 1TB was getting full, I decided to order two 2TB disks, put them in a RAID-0 config and clone the current RAID-0 1TB config to the new 4TB config using dd. However, things didn't quite work out the way they should be.. When I looked in GParted, I saw only 1.64TiB of the array was being detected, but the independent disks were shown with their full 2TB. Does anyone know how I can fix this? Here are some screenshots to show you what GParted shows me:
[[IMG]http://tweakers.net/ext/f/fQuJh3mBOmzgUmguqmnIF476/thumb.jpg[/IMG]]("http://tweakers.net/ext/f/fQuJh3mBOmzgUmguqmnIF476/full.jpg")

Thinking this must be just some glitch in GParted, I started the dd operation anyway, however to my disappointment, the dd operation didn't quite work out the way it should be either: instead of writing everything from my old array to my new one, it just wrote everything to the first disk of the new array instead to the array as a whole. Again, here are some screenshots (I've tried some fiddling with the RAID controller by breaking the array etc. so the /dev/mapper/ name is different, however just pretend it's the same one as in the above screenie):
[[IMG]http://tweakers.net/ext/f/9NWVZftzBRyYnnP49SiHPE19/thumb.png[/IMG]]("http://tweakers.net/ext/f/9NWVZftzBRyYnnP49SiHPE19/full.png") [[IMG]http://tweakers.net/ext/f/G7KanWumI0DvmnUp7D7gCfiy/thumb.png[/IMG]]("http://tweakers.net/ext/f/G7KanWumI0DvmnUp7D7gCfiy/full.png") [[IMG]http://tweakers.net/ext/f/xvqQdbHyOr8tUmmrf5ce2YzZ/thumb.png[/IMG]]("http://tweakers.net/ext/f/xvqQdbHyOr8tUmmrf5ce2YzZ/full.png") [[IMG]http://tweakers.net/ext/f/9NKuw0QUotE8LVwF4nsLim6l/thumb.png[/IMG]]("http://tweakers.net/ext/f/9NKuw0QUotE8LVwF4nsLim6l/full.png")

I'm not a Linux guru (using Win7 as my main OS), but I know my way around Linux. However I have absolutely no idea what is causing this... I hope someone here knows what's happening :)
[/SIZE]

---

### Post by Bitage on 2011-07-02
*bump*
Anyone? :(

---

### Post by dabl on 2011-07-02
I'm thinking dd was not the tool to use -- I think you _did_ clone your old RAID, exactly, including the size of it.

I would re-make the new RAID with the new drives -- you can make a new partition table on each of them and reformat them individually if needed.  Then find a way to copy the data, (not the image) off the old RAID to the new one.

---

