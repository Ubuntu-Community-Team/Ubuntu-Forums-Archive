---
title: "Uninstalling"
date: 2005-11-25
forum: General Help
---

### Post by gonzo409 on 2005-11-25
Hi,

I thought I would give Ubuntu a try, and I went ahead a followed the instructions at this page for installing: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Unfortunately, I encountered numerous bugs during installation and now when my PC boots to Ubuntu, I get this:

"Configuring the base system
Use of unitialized value in substitution..." and a repeating error that ends in 
Id "1" respawning too fast disabled for 5 minutes. I looked around on the forums and tried a few things to fix this but to no avail.

It seems my Ubuntu installation got completely borked, so, I would like to remove Ubuntu for my PC and reclaim the partition space I set aside to run Ubuntu. Basically, I just want everything on my PC back to the way it was before I even thought about installing Ubuntu. Any ideas on how I can get started?

---

### Post by taurus on 2005-11-25
I am not sure what your system was like before you installed ubuntu but when you install another OS, just temm it to remove all the partitions and create whatever you want after that...

---

### Post by kalin on 2005-11-25
Also you can boot from the live CD and take a look at GParted. Applications->System Tools->GParted.

It's a partition manager, you can use it to remove all Ubuntu partitions.

---

### Post by gonzo409 on 2005-11-27
I cannot get GParted to run from the LiveCD.

Perhaps I can boot from the Breezy Badger CD and delete the partitions tht I created in the first place? Originally, I had a 30 gig partition for Windows XP, but a little over 10 gigs was unused so I used that to create a new partition for Ubuntu and some swap space.  Forgive the ignorance, but I've never dealt with partition management before and don't want to screw up anything.

---

### Post by kch_86 on 2005-11-28
you can reformat the partition that Ubuntu was on in Windows XP. Just go to control panel->administrative tools->component management->disk management and then the Ubuntu partition and swap partition will be the **non NTFS** partitions. just right click these, delete them, and then reformat them.

---

