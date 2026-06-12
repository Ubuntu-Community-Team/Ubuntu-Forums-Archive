---
title: "Messing with partitions"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by winol5 on 2009-05-17
Ok, here's the thing, I have a laptop actually with 3 partiticons, 1 swap, 1 ntfs (xp), 1 ext3 (ubuntu 9.04), but my windows is very crappy right now, I will backup my files and reinstall it (maybe I could install winodws 7, I dont know...), but I have an idea so this kind things can't happen again, could I just make a 100 gb partition (NTFS) for files and programs, 1 for ubuntu (like 15 gb) and 1 for windows (15 gb also) and that both OS share the data partition and install both kind of programs (ubuntu and windows ones) without messing with filetype issues?

Or what do you recomend me to do?

Thx

---

### Post by winol5 on 2009-05-17
No one? :S

---

### Post by Mark Phelps on 2009-05-17
You need to have more patience, for starters.  It's considered rude to bump a post more than once in 24 hours.  Waiting only one hour to bump it only shows your impatience.

Also, it's hard to tell what you really want to do.

You can share files but not programs between Ubuntu and MS Windows.  So, if you want to put data on a shared NTFS partition, that will work, but you're most probably not going to be able to run the same programs in MS Windows and Ubuntu -- even if you do install Wine, which is a whole 'nother set of problems.

Best short-term solution is to have an OS partition for XP, OS and Swap partitions for Ubuntu, and a shared NTFS partition for holding data.

You will have to use manual partitioning to set it up.

---

### Post by winol5 on 2009-05-17
yeah I dont pretend to run win programs in ubuntu or viceversa just to hold the files for running them together I mean, install office in the data partition and also install openoffice (ubuntu version) in that partition, using the corresponding OS for each of them to run, what I was concerned was about installing ubuntu programs in a NTFS file system (I dont know which extension they are but I mean the equivalent to the exe and dat ones)

And sorry for bumping :(

---

### Post by mättu on 2009-05-18
As I am not completely aware of what you precisely want to do, I would suggest to do a web search for terms like
ubuntu windows dualboot
or
ubuntu xp vista multiboot
There are tons of really good guides in all flavours: From screenshot based step-by-step guides to more tech-savvy commandline oriented pages.
Feel free to post back if you can't find what you need.

cheers
:m)

---

### Post by Mark Phelps on 2009-05-18
> **winol5 said:**
> yeah I dont pretend to run win programs in ubuntu or viceversa just to hold the files for running them together I mean, install office in the data partition and also install openoffice (ubuntu version) in that partition, using the corresponding OS for each of them to run, what I was concerned was about installing ubuntu programs in a NTFS file system (I dont know which extension they are but I mean the equivalent to the exe and dat ones)

And sorry for bumping :(
You can't install Ubuntu programs in NTFS partitions, so you won't be able, using your example, to install the Linux version of OpenOffice in the shared NTFS partition.

However, using the package ntfs-3g, you can read and write NTFS partition files using Ubuntu.  So, you can use MS Office and OpenOffice both on the same files.  Just make sure when you save the files using OpenOffice that you don't change them to OpenOffice format.

---

