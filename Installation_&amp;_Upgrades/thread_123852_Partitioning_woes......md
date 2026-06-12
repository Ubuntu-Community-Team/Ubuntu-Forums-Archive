---
title: "Partitioning woes....."
date: 2006-01-31
forum: Installation &amp; Upgrades
---

### Post by Killgore on 2006-01-31
I am looking to dual-boot my system with windows XP and ubuntu 5.10

I have an 80gb hard drive that has 5gb allocated to XP, and was hoping to set up a ubuntu install and a shared partition (fat32). But the problem i am having lies in setting up a more advanced partitioning system. I would like to have seperate partitions for the following places (and my planned sizes):

/ (2gb)
/boot (200mb)
/usr (?)
/var (?)
/home (2gb)
/swap (300mb)

/Shared (Remaining space)

Will this setup allow me to have a fully functional ubuntu setup with room to install programs? I dont really need many so would it be worthwile to forgo the /usr partition?

---

### Post by linuxden on 2006-01-31
[QUOTE=Killgore]Will this setup allow me to have a fully functional ubuntu setup with room to install programs? I dont really need many so would it be worthwile to forgo the /usr partition?[/QUOTE]

If this is your first time with Linux perhaps you should look into only using one partition for your  linux / (root) + its swap... so you dont have to delve into extended/logical partitions.

also you will need to create a FAT32 partition to share your files between win/ubuntu. (i assume your /shared partition was refering to this)

The above setup i just gave you is the one most users use to creat a dual boot...
The only advantage of doing the way you have described is that in case of damage or to upgrade its makes it a lot easier to recover/upgrade...

---

### Post by Killgore on 2006-01-31
Well i am a bit of a linux novice but i have experince with filesystems and windows.

So maybe a revised setup would be like this:

/Windows (5gb)

/ (3gb - Will this be enough? And i assume i will have to set it as bootable in the partion manager)
/swap (300mb)
/home (1gb)

/Shared FAT32 (Remaining)

This would allow me to keep all my settings seperate and also not have to worry about logical partions - exactly 4 partions! \\:D/ 

EDIT: Looks like i cant count :( I guess ill have to make / a primary partion and /swap,/home logical or is it extended?

If i have made any mistakes with this could people please correct them?

---

### Post by Herman on 2006-01-31
Welcome, killgore, will [this]("http://users.bigpond.net.au/hermanzone/p14.htm") help you? Or [this]("http://users.bigpond.net.au/hermanzone/p3.htm")? Maybe you'll need to combine them both. :D (Herman)

---

### Post by Killgore on 2006-01-31
Thanks a lot herman. I have now gone back on my plan to set up an advanced partion system as it seems to much hassle for what i need to use this box for. Thanks for the help every1.

---

### Post by linuxden on 2006-01-31
Great info Herman... Nice How-to's

---

### Post by Titus A Duxass on 2006-01-31
Great Job Herman, now we just have to persuade people partion like this.  

There is nothing to be scared about partitioning.

---

### Post by linuxden on 2006-01-31
Why do you need to persuade anyone on how to partition "there" computer???

isnt the beauty of linux that it is customisable to ones desires?? 

scary thing i just read and i wanted to bring it to your attention...

---

