---
title: "Ubuntu Reinstallation"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by sambit on 2009-08-21
Hi..
I use dual boot xp/ubuntu.I allocated 4 gb of space for ubuntu. Now i want to expand to 10 gb. Can u help me out with these choices and recommend a better solution if u have one. :)

a. Reinstall ubuntu and allocate more space.
b. Allocate a separate partition as download and installation drive.(For Synaptic Package Manager)

Thanx in advance :D

---

### Post by starcraft.man on 2009-08-21
No need to reinstall friend. Not when.........*unveils* gparted is around. *don's TV salesman voice* This software does it all, it moves, makes and deletes, even resizes partitions. You want a new partition table, bam! You want to format a partition. Two clicks and your done. It's the greatest, call now for our special 20 for 1 price of 5 bucks. If ya manage in the next five minutes, ya get all copies for FREE. You hear that, wait what? Are you writers smoking something? CUT!

Being more serious, see gparted [documentation]("http://gparted.sourceforge.net/documentation.php") for more information on how to manipulate partitions. I'd advise you to take freespace from a partition and just merge it into your existing one, painless. Please, as always, I caution that even though most partition edits go fine without error, backup data just in case, especially stuff you would die without. Read the how to guides going down, if you've any questions after just reply. Gparted is available on the livecd btw, see System Menu > Admin > Partition editor.

You might also want to think of making a separate /home partition. See [here]("http://www.psychocats.net/ubuntu/separatehome") for reasons and how. Especially if your planning an extended stay.

Remember.... you've only 4 minutes left, call now!

---

### Post by raymondh on 2009-08-21
> **starcraft.man said:**
> No need to reinstall friend. Not when.........*unveils* gparted is around. *don's TV salesman voice* This software does it all, it moves, makes and deletes, even resizes partitions. You want a new partition table, bam! You want to format a partition. Two clicks and your done. It's the greatest, call now for our special 20 for 1 price of 5 bucks. If ya manage in the next five minutes, ya get all copies for FREE. You hear that, wait what? Are you writers smoking something? CUT!
 Especially if your planning an extended stay.

Remember.... you've only 4 minutes left, call now!

LOL.

@ starcraft.man ... you've been watching the shopping network/channel too long, too much :)

---

### Post by starcraft.man on 2009-08-21
> **raymondhenson said:**
> LOL.

@ starcraft.man ... you've been watching the shopping network/channel too long, too much :)

Not just tv!

Well, sure, but not in our dreams. Only on TV and radio... and in magazines... and movies, and at ballgames, and on buses, and milk cartons, and T-shirts, and bananas, and written in the sky. But not in dreams, no sirree.

Maybe I watch Futurama too...

WHAT? Blasphemy, never enough Futurama! NEVER!

---

### Post by sambit on 2009-08-25
thanks..... going to try out ur suggestion :D

---

### Post by sambit on 2009-08-25
i am new to ubuntu and all the resizing stuff looks strange to me.
Can u give some more links to gpart OR tell me how to install a fresh copy of ubuntu..
i could erase the partions from xp but there will be boot problems.

---

### Post by sambit on 2009-08-26
I want to extend my current root partition size to +4GB. i cant seem to do that with gpart... help plz

---

### Post by Bartender on 2009-08-26
sambit -
More details please.  Do you mean you're booting from your Ubuntu LiveCD, then from the desktop you go into Administration>Partition Editor?  

Do you have any details as to what it's not doing?  Error messages, etc.?

I sound like a broken record, but the GParted LiveCD works so much better.

---

### Post by raymondh on 2009-08-26
> **sambit said:**
> I want to extend my current root partition size to +4GB. i cant seem to do that with gpart... help plz

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Remember that when using gparted from the liveCD,  ensure that the partitions are *indeed* unmounted (rt. clk, on partition and if given option to unmount, do so).  Also, select swapoff for swap (if available)

---

### Post by sambit on 2009-08-31
sorry was busy so didnt reply earlier...used gparted but there was no option of resizing...
dont know what a live CD is so i formated ubuntu and resized during formating..no probs dual boot runs.... fine thanks to everyone who helped me out

---

### Post by sambit on 2009-08-31
> **starcraft.man said:**
> Not just tv!

Well, sure, but not in our dreams. Only on TV and radio... and in magazines... and movies, and at ballgames, and on buses, and milk cartons, and T-shirts, and bananas, and written in the sky. But not in dreams, no sirree.

Maybe I watch Futurama too...

WHAT? Blasphemy, never enough Futurama! NEVER!
lol & Thanx a ton

---

