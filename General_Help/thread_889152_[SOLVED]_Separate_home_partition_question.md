---
title: "[SOLVED] Separate home partition question"
date: 2008-08-13
forum: General Help
---

### Post by petedct on 2008-08-13
I have read about the benefits of creating and using a separate home partition in places such as  [psychocats]("http://www.psychocats.net/ubuntu/index.php") and [Full Circle Magazine]("http://fullcirclemagazine.org/"). I'm convinced that it's the way to go but I do have one question. What happens to all those hidden folders and config files in my home folder? Will they mess up a fresh install? For example, when I move up to Intrepid I'm planning on reformating the root partition leaving the home partition untouched. Intrepid will be cleanly installed into root but the hidden folders and config files in my home folder will remain. Will these Hardy leftovers create problems for the new versions of the apps that will come with Intrepid? If so is there a way to handle this? Thanks for your consideration.

---

### Post by pytheas22 on 2008-08-13
No, the configuration files shouldn't cause any problems.  I've used a separate /home since Feisty, I'm now on Hardy (have upgraded via clean reinstalls of the root partition each time) and have never run into problems.  Besides, in a worst case, you could always clear out a configuration folder by renaming or deleting it, and the application that uses it would create a fresh default profile for you.

The only conceivable issue that I can think of is configuration folders that get orphaned because no application uses them anymore (i.e., because the application is no longer a part of Ubuntu), but that doesn't hurt anything besides occupy a negligible amount of disk space.

---

### Post by Oldsoldier2003 on 2008-08-13
> **petedct said:**
> I have read about the benefits of creating and using a separate home partition in places such as  [psychocats]("http://www.psychocats.net/ubuntu/index.php") and [Full Circle Magazine]("http://fullcirclemagazine.org/"). I'm convinced that it's the way to go but I do have one question. **What happens to all those hidden folders and config files in my home folder? Will they mess up a fresh install?** For example, when I move up to Intrepid I'm planning on reformating the root partition leaving the home partition untouched. Intrepid will be cleanly installed into root but the hidden folders and config files in my home folder will remain. Will these Hardy leftovers create problems for the new versions of the apps that will come with Intrepid? If so is there a way to handle this? Thanks for your consideration.

**In a word, no. In more words, maybe.** What I mean by this is if you are reinstalling the same version and everything worked before, the settings "should work". In practice you only really need to worry about it not working when you switch distributions or when there is a major change in application versions.(Occasionally this can create issues if the configurations are incompatible between versions)

Personally I prefer to go with a shared DATA partition and making all installations "clean".

---

### Post by petedct on 2008-08-13
> **Oldsoldier2003 said:**
> **In a word, no. In more words, maybe.** What I mean by this is if you are reinstalling the same version and everything worked before, the settings "should work". In practice you only really need to worry about it not working when you switch distributions or when there is a major change in application versions.(Occasionally this can create issues if the configurations are incompatible between versions)

Personally I prefer to go with a shared DATA partition and making all installations "clean".

A shared DATA partition when dual or multi-booting correct?

---

### Post by Oldsoldier2003 on 2008-08-13
> **petedct said:**
> A shared DATA partition when dual or multi-booting correct?

correct. the only issue you may run into is you need to allow for the fact that RH based distros start the initial account with UID 500 Debian based distros at 1000. So for optimal file sharing abilities  dont install the additional distros using your username. While possible to switch UIDs I'm just more comfortable with creating a new user and assigning it the uid to match your Ubuntu install.

---

### Post by louieb on 2008-08-13
> **petedct said:**
> A shared DATA partition when dual or multi-booting correct?

I use a  data partition for  PCs that run a single OS  doesn't matter what OS. I like to keep my data separated from the operating system.  
For a Linux only PC I use 4 partitions

[LIST=1]
[*]/ root 7-10GB
[*]/home 2-5GB
[*]/data  the rest of the drive.
[*]swap  .5GB unless I need to hibernate  then 1.5 x installed ram.
[/LIST]

---

### Post by Oldsoldier2003 on 2008-08-13
> **louieb said:**
> I use a  data partition for  PCs that run a single OS  doesn't matter what OS. **I like to keep my data separated from the operating system.  **
For a Linux only PC I use 4 partition

[LIST=1]
[*]/ root 7-10GB
[*]/home 2-5GB
[*]/data  the rest of the drive.
[*]swap  .5GB unless I need to hibernate  then 1.5 x installed ram.
[/LIST]

+1 

Keeping data separate from the OS is a prudent practice in my book

---

### Post by bodhi.zazen on 2008-08-13
+1 Oldsoldier2003

Although rare, in your config files in /home/user_name conflict or your UID (ID #, not name) conflict you can have problems.

On you set it up, I think you will find a shared data partition is quite easy.

If you share /home, just use unique user names on each os.

---

### Post by petedct on 2008-08-13
I guess everyone is talking about partitioning the drive similar to the yellow FAT32 shared data partitions shown [here]("http://www.psychocats.net/ubuntu/partitioning"). I've used that set up when duel booting XP and it has worked well for me.

Thanks everyone for your replies.

---

