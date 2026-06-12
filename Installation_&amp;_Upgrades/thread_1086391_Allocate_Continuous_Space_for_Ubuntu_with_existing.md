---
title: "Allocate Continuous Space for Ubuntu with existing Windows"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by flylehe on 2009-03-04
Hi,
I am about to reinstall Ubuntu on my laptop where Windows XP already exits. 

Someone told me before that the space allocated for Ubuntu must be continuous, which is shown in a colorful bar in partition step of the Ubuntu installation. In the bar of my case, from left to right are:

Windows RAM --- Windows C (system) disk --- Windows D (data) disk --- my current Ubuntu home  --- my current Ubuntu root  --- my current Ubuntu swap. 

I am now hoping to add some space from Windows C into new Ubuntu root and it would be the best if the content in my current Ubuntu home could be preserved after the reinstallation. I was wondering if the one who told me is correct. If he is, I will not able to make space from Windows C for new ubuntu root? If he is not, how shall I do to achieve my goal?

Thanks in advance!

---

### Post by Partyboi2 on 2009-03-04
If you are just wanting to increase the size your your / partition you can boot a ubuntu live cd and use gparted (system>Admin>Partition Editor) and use the resize option to shrink your windows partiton and increase your / partition. Saves having to reinstall the operating system. If you do decide to use the resize option backing up your important stuff is recommended.

---

### Post by flylehe on 2009-03-04
Thank you! My Ubuntu has some problem hard to fix, so I have to reinstall it anyway.
My concern is that if Windows C disk is separated from current ubuntu root by Windows D disk and current ubuntu home, as shown in the partition step of installation of Ubuntu, is it possible to add some space from Windows C to Ubuntu root? As I heard from someone that since Windows C is not adjacent to Ubuntu root, it is impossible.

---

### Post by Mark Phelps on 2009-03-04
Basically, no -- a partition can't span gaps.  Say you have partitions in order, #1, #2, #3 and you want to "move" space from #1 to #3.  To do that, you would have to do the following (in order):
1) Shrink #1 to create some empty space
2) Move #2 to the left to take up the slack created by shrinking #1
3) Expand #3 to use the new space created by moving #2.

You can do all of these using the GParted LiveCD -- which is the better approach because that way, none of your partitions will be mounted.  It's just VERY SLOW!!! Be prepared for this to take some time (maybe an hour, maybe more) and do NOT interrupt it while it's working.

---

