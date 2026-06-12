---
title: "Help with partition please?"
date: 2008-12-05
forum: Installation &amp; Upgrades
---

### Post by Mangwhop on 2008-12-05
Hi all,


      Im a newbie. I just installed Ubuntu and didnt partition my harddrive and lost windows. I originally wanted to dualboot with windows xp and Ubuntu. Anywhooo... I tried Gparted but it wount let me unmount or do anything.. heres what i get (see attached photo)

I want to create a partition now for windows.

---

### Post by Partyboi2 on 2008-12-05
Make sure you are using a live cd, either a ubuntu live cd or gparted live cd, then right click on the partitions you want to work on and choose to unmount..

---

### Post by Mangwhop on 2008-12-05
Would the disk i created to install Ubuntu be considered a "live" cd? 

Im very new to this so please have patience  :)

---

### Post by Nathan Sweeney on 2008-12-05
> **Mangwhop said:**
> Would the disk i created to install Ubuntu be considered a "live" cd? 

Im very new to this so please have patience  :)

Yes, it is a Live CD, meaning that you can run the OS (Ubuntu) Live, of the CD (well, unless you got an alternate install cd...).

I'd say the easiest thing to do at this point, since you are starting fresh, is to install Windows first.  When you install windows, delete all partitions and then create a new one whatever size you want, leaving some free space for linux.

Once Windows is installed, then install Ubuntu and make sure you choose "Manually Partition" or "Use free space" so that it only uses the space left over from the windows install.

---

### Post by DLF44 on 2008-12-05
if i choose the "guided - use entire disk" partition, is that permanent? and also does it wipe out all of my files from windows? or is there a way to transfer them into ubuntu?

---

### Post by Nathan Sweeney on 2008-12-05
> **DLF44 said:**
> if i choose the "guided - use entire disk" partition, is that permanent? and also does it wipe out all of my files from windows? or is there a way to transfer them into ubuntu?

The simple answer is yes, it wipes out all of the files and they are gone.

The complicated answer is that you can sometime recover deleted files (CSI-ish :)) with some tools in Linux.

If you want to transfer files in linux, your best option is to shink down the Windows partition, then install ubuntu in the freed space.  From Ubuntu, you can easily access your windows partition.

---

### Post by DLF44 on 2008-12-05
on the slider it wont let me move the windows partition below 79% (111.3 gb)

i would mainly be using ubuntu, but would like to get my files into ubuntu from windows.

---

### Post by Nathan Sweeney on 2008-12-05
> **DLF44 said:**
> on the slider it wont let me move the windows partition below 79% (111.3 gb)

i would mainly be using ubuntu, but would like to get my files into ubuntu from windows.

Did you defrag first?  How big is your drive?  How much data do you want to transfer?

You can always install ubuntu and then delete the windows partition and resize the ubuntu ones, though you will have to use a live cd to do that (can't use partitions that are in use).  I like [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) for this.

---

### Post by DLF44 on 2008-12-05
i didnt defreg first, should i do that? are there any other things that i should do first?

my hardrive is 160gb

---

### Post by Nathan Sweeney on 2008-12-05
> **DLF44 said:**
> i didnt defreg first, should i do that? are there any other things that i should do first?

my hardrive is 160gb

Defrag may allow you to shrink the windows partition more.  It will keep the files together, so it can shrink around them more.

---

