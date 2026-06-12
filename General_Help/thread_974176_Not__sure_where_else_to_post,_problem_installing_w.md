---
title: "Not  sure where else to post, problem installing windows after linux."
date: 2008-11-07
forum: General Help
---

### Post by Akuseru on 2008-11-07
I've used xp for a long time ,but recently tried ubuntu after I was having some troubles with xp. And for my main pc, it turns out it just doesn't fit my needs, so I 'm going back to xp. Or trying. Whenever I try to setup xp, I can get the setup screen to start, where it formats/copies over all the other files, but when it reboots my pc, to install xp for real, it just freezes. A black screen, with a single under line. Does linux do something to a hard drive that'd make it do this? It always worked before, with this exact xp disk.

Sorry if this isn't a good place to post this, I'm completely out of ideas of my own.

---

### Post by DGZDGZ on 2008-11-07
Alright mate. Is it the full install your trying or the quick option?

---

### Post by Akuseru on 2008-11-07
What do you mean, was it the full installation of linux? Originally, yes.

Or do you mean a full format? I've tried both...

Sorry if I'm not following..

---

### Post by oilchangeguy on 2008-11-07
> **Akuseru said:**
> I've used xp for a long time ,but recently tried ubuntu after I was having some troubles with xp. And for my main pc, it turns out it just doesn't fit my needs, so I 'm going back to xp. Or trying. Whenever I try to setup xp, I can get the setup screen to start, where it formats/copies over all the other files, but when it reboots my pc, to install xp for real, it just freezes. A black screen, with a single under line. Does linux do something to a hard drive that'd make it do this? It always worked before, with this exact xp disk.

Sorry if this isn't a good place to post this, I'm completely out of ideas of my own.

are you using a true xp cd, or a factory restore cd? with the true cd, boot from it. follow the prompts to install windows. when you get to the partiton part it will show several partitons (linux) already there. delete each of these partitions. then format the entire unallocated space. don't use the quick format.

---

### Post by Akuseru on 2008-11-07
A true xp cd. And that's what I do, I delete everything that has linux on it. The hard drive is split into two sections right now, 15gb of nothing, which is where I "try" to install xp, and the rest is all data I have. I do try it with a full format. But after xp formats the drive, and copies the files over, it'll restart the pc to begin installation. At that point, installation DOESN'T start, that's the problem. It either just tells me to press any key to boot from cd, etc, which just leads me back to formatting and such, or, with no cd in, a black screen with one line in the upper left hand corner, as if it's gonna load, but, no matter how long I wait, it doesn't.

---

### Post by whitethorn on 2008-11-07
Don't know if this makes a difference.  Have you tried starting the computer with the xp cd in, but not pressing a key when it prompts you to?  As far as I remember XP copies the files over it then restarts and configures itself.

---

### Post by Akuseru on 2008-11-07
With the cd in, It just continues to prompt me to press any key. If I wait, it'll get to Five (I believe) dots, then freeze. It doesn't continue from that point, and pressing any key does nothing, and I have to restart. 
Without the cd in, I get a blank screen, as I said.

---

### Post by Akuseru on 2008-11-07
Bump.

---

### Post by Nabanna on 2008-11-07
If you dont need Linux onto your system, you first need to delete the Linux Partitions either from 'start -> Control Panel -> Administrative Tools -> Computer Management -> Disc Management' and there find and delete Linux partition(take extreme caution while doing this) or boot from XP disc and delete Linux partitions from there(and create new partitions if you desire).
Then (for problem free installation)first delete the partition on which you want to install XP, create New(raw) partition(preferably C) and proceed for installation.
Once the installer formats the drive and copies the files to that drive it will Restart, after Restart do not let your PC boot from CD, then i think installation for XP will continue.

---

### Post by Akuseru on 2008-11-07
That's what I do. Everytime. I don't let it boot from the cd, and it just freezes at that stage, doesn't go on. One thing though. The old, storage partion of the hard drive used to be d, but after installing linux, it's c now. How do I switch that/does it matter?

---

### Post by TeXtonyx on 2008-11-07
copy

---

### Post by TeXtonyx on 2008-11-07
I think you will have to format the entire disk, which will mean
backing up your data to cd/dvd or usb sticks. You can doublecheck
on Usenet: microsoft.public.windowsxp.general or the Microsoft 
news server: news.microsoft.com and find the English XP forum or

[http://groups.google.com/group/](http://groups.google.com/group/) [paste into browser in one line]
microsoft.public.windowsxp.general/topics?lnk

Also is your 15 GB unallocated space at the beginning of the hard drive
or does it come after the data? I've never installed XP on the second
partition of a drive, so I don't know if its possible. ... Most likely
I think it is the type of MS install cd you have. Some will do upgrades
and others require a clean install to the drive.

---

### Post by Akuseru on 2008-11-07
I believe it's at the beginning...This same cd has always worked for me, unless linux changes something..which it must of, considering it doesn't work now.

---

### Post by Nabanna on 2008-11-08
> **Akuseru said:**
> That's what I do. Everytime. I don't let it boot from the cd, and it just freezes at that stage, doesn't go on. One thing though. The old, storage partion of the hard drive used to be d, but after installing linux, it's c now. How do I switch that/does it matter?


It shouldn't matter(but generally it is C though).
You must check your Windows CD, but from your posts it seems its ok, because if its not then installation process should have been halted while copying installation files after formatting (or like anywhere in between the installation steps).

> **Akuseru said:**
> I believe it's at the beginning...This same cd has always worked for me, unless linux changes something..which it must of, considering it doesn't work now.

I suspect Linux has changed anything, however while you install Windows, it shows Unpartitioned space at bottom(of the List of partitions), you can create partition and use this partition for Windows, dont touch any other partitons, just give it a try.

---

