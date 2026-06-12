---
title: "Hard drive arrived.  Setting up and need advice."
date: 2008-07-17
forum: General Help
---

### Post by Phastor on 2008-07-17
Ok.  I created a thread a few weeks ago regarding where and how I should store my collection of media and documents I have aquired over the years.  I've been playing with Ubuntu on my laptop for a while. Now I am migrating from XP to Ubuntu on my desktop and needed advice.  Here's an update. I ordered a 640GB WD SE16 drive and it arrived today. Here's what I'm planning to do.
 
After thinking about how my mind works with filekeeping and with what was said here, I'm going to set up a 150GB to 200GB partition for the OS and apps. The rest of it will be set off in a storage partition where I will have my /home directory and a /storage directory where I will dump all of my media and documents. This way I can save a lot of grief by keeping my settings and files on their own partition if I ever reinstall or try out different distros.

Given my history in file management this seems like a setup I can adapt to easily. Will I run into any problems later on down the road where I will regret doing things this way? I'm also open to any suggestions that could make this setup better or more practical. Thanks!

---

### Post by jonian_g on 2008-07-17
No you won't run into any problems. But I wonder why you want to create a /storage (you mean /media/storage) partition? You can keep your data inside the /home partition in a folder.

The only problem you might have is mounting partitions, so there's my tip

Install "Storage Device Manager" from add/remove. After installation it is at System>Admin>Storage Device Manager.
Click the "Assistant" button to enable automount on boot, have write permissions etc.

---

### Post by danwood76 on 2008-07-17
With regards to the amount you are setting aside for your OS and Apps.
I think you are alotting a bit too much.

I normally allow around 15 - 25GB for my main OS and Apps, 80GB for my /home and I have a 1TB storage drive for my data.
I have never come close to filling that 25GB.
If you really want a lot of storage space I would try 50GB for / which will give you a lot more space for your personal files.

Also if you want a seperate /home and /storage you will need a partition for each.
Or as jonian_g said just create a /storage within your /home or your actual home folder.

---

### Post by mannheim on 2008-07-17
Like danwood76, I would vote for 25GB for the OS and applications. Another thought is: set aside another 25GB for a spare partition, formatted for a linux filesystem. Somewhere down the road, it is always useful to a spare partition, perhaps for installing a new OS alongside the old.

---

### Post by Phastor on 2008-07-17
Apparently I misunderstood what happens when you create a partition for /home.  Before reading the replies here I was under the impression that when you created a partition for /home, the actual /home folder was placed within the partition.  That's why I was saying I wanted /home and /storage in the same partition.  I thought the /home folder was put into that partition.  However after reading this, if I understand correctly, the entire partition is considered /home?

Also, the reason why I wanted to create the large partition for the OS and apps is because I plan to be running (or attempting to run) some games through Cedega.  With some games reaching up to 10 gigs a pop, I figured 100-150GB would be necessary.

---

### Post by danwood76 on 2008-07-17
Yes the partition is mounted to /home, so within your / there will still be a home directory but your partition will be mounted there.
Each time you mount a filesystem in linux it is mounted to a folder within / somewhere, for example USB drives are mounted to the folder /media/disk.
I hope that makes sense to you.

Cedega is a derivitive of WINE and I think you normally store wine software within your home folder.
So you might be better off allocating all that extra space to /home, I've never used cedega so you may have to look into where it puts its virtual C drive.
You could even create a partition purely for the storage of your games, the possibilities are endless ;)
I hope I havent confused you in what I have said.

---

### Post by evets25 on 2008-07-17
The way I have it set up, I have one smaller 80Gb drive for my "/" folder, then I have a large partition on my 500Gb drive, which is mounted at "/home/username/storage". Well, it's actually more complicated than that with the partitions for /boot and swap, but that's the basic idea. So when I go to re-install, I back stuff up to my storage folder, and then blow away the main partition, which includes root and all of home except "~/storage". Storage is also where I keep most of my stuff, like movies and music and documents and such. Mounting your storage partition to a folder in your home directory makes a lot more sense to me rather than making a new folder in the root partition. By doing "/storage" rather than "~/storage" you may run into things like problems with permissions, and besides, since it's *your* documents, and not the system's documents, it only makes sense, IMHO.

---

### Post by Phastor on 2008-07-17
Ok.  So now that I correctly understand how mounting a partition to /home works (thank you, danwood, for clarifying that for me) I've decided that the best approach for me will be to go as planned by mounting the large partition to /home (I'll read the tutorial that has been posted in my last thread) and then creating ~/storage within /home/<user> somewhere.  I'm so used to my media and documents having their own dedicated partition while running Windows.  I've had it like that for several years, but that's something I can get over.  Not a big deal.

I'll have to check and see where Cedega puts the virtual C: drive.  I knew that Wine put's it's drive in /home, but I'm not sure about Cedega.  If it puts it in /home like Wine does I'll just give the OS and apps 25-30GB like most of you have stated.  Cedega might even give an option of where to put it. Then I would be set.

---

### Post by jonian_g on 2008-07-17
> **Phastor said:**
> Ok.  So now that I correctly understand how mounting a partition to /home works (thank you, danwood, for clarifying that for me) I've decided that the best approach for me will be to go as planned by mounting the large partition to /home (I'll read the tutorial that has been posted in my last thread) and then creating ~/storage within /home/<user> somewhere.  I'm so used to my media and documents having their own dedicated partition while running Windows.  I've had it like that for several years, but that's something I can get over.  Not a big deal.

I'll have to check and see where Cedega puts the virtual C: drive.  I knew that Wine put's it's drive in /home, but I'm not sure about Cedega.  If it puts it in /home like Wine does I'll just give the OS and apps 25-30GB like most of you have stated.  Cedega might even give an option of where to put it. Then I would be set.
Cedega creates many virtual C: drives. You can create a virtual drive for every game you install, so you can use different config for every game. All these virtual drives go to /home/user/.cedega/

example:

/home/jonieno/.cedega/Need for Speed/c_drive

I was used too, when using windows, have a dif partition for data. But having just /home as a dif partition is better, because you have your data and your configuration together.

---

### Post by Phastor on 2008-07-19
Well it's done.  I have Ubuntu set up on a 30GB partition with a 600GB partition mounted as /home.  I left 10GB remaining on the drive for whatever reason in the future I might want to try with it.  For now it's all being used as swap.

Thanks for all the help here.  I'm still trying to work out some bugs with sound and video, so if anyone feels like helping this new guy out a little more you can head to another post I made about that. [http://ubuntuforums.org/showthread.php?p=5416252#post5416252](http://ubuntuforums.org/showthread.php?p=5416252#post5416252)

Thanks again for all the help.

---

