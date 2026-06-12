---
title: "Optimal Hard Drive Setup"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by Sticks_uk on 2009-08-24
Ok so I would like to set up my hard drive with mutiple partition without loosing to much space in the process.

I would like to set up my hard drive like this

C: Win XP 64bit
D: Windows Games
E:/Home Filesystem for ubuntu
F:/User For Torrents and other stuff
G: Ghost image for both operating systems
H: Page file for ubuntu (I have 4gb of RAM)

I only have a 500gb hard drive and would like to use ubuntu as my main OS just need to be able to run games in windows (not via WINE nor VM)

What sizes should I use ?  

I may combine C: and D: as I only intended to play Aion on windows.

I hope that this is the last time I need to set up this hard drive unless it dies and i need to get a new one.

thanks in advance.

---

### Post by starcraft.man on 2009-08-24
Where is your / partition? Also, by user are you referring to /usr that's an important directory and ya can't just mount over it or use it for storage. Lastly, ya reference them as a C, D... this is only on Windows. In linux world, partitions take on name of the mount point your mounting to. Usually the label, assigned to it at creation of partition.

Notes on your proposal: First two should be primary partitions I suppose, the rest should be in an extended partition. You seem to be confusing the mount points, / is for storing the main directory and subdirectories important. Then other partitions can be made to separate other directories, like /home which holds your user data, configurations and other data like music and movies. /user is not a directory, /usr is a directory for important data don't mount over in setup.

As to how much you need, the following sizes should be a guide. No more than 500MB swap is required since you've so much RAM. A root partition / only requires about 6-9 GB over a lifetime install including upgrades, other kernles, other software. That's a large overestimation btw, standard install of linux is 2.5 GB, my range is buffer for everything else you'll install plus some room for temp files. /home can be as large as ya want, by default it should be as big as the files ya plan to store in are. If your gonna put lots of vids on the partition it needs to be like 50GB, if your storing them in windows partitions then just 10GB of room would be enough for stuff ya download. Userconfigs are just text files, don't take more than a few hundred MB. The rest of the sizes left over for Windows and other partitions up to your needs, I provided minimums here feel free to add more.

As to Partitioning (> is primary -> is extended and logical):
> Windows Install
> Games
-> Extended Space
--> / directory
--> /home
--> swap
--> ghost files

If ya need additional assistance, see gparted [docs]("http://gparted.sourceforge.net/documentation.php") and use gparted from a live CD for this. See old section, read general on down. That's about it, any questions reply. Partitioning ain't hard, but is nuanced. Also, for the love of everything, backup anything essential before partitioning, no one on these forums is responsible for your data. Just you.

---

