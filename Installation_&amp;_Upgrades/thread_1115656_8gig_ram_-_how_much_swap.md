---
title: "8gig ram - how much swap?"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by derWalter on 2009-04-04
Hi folks.

im wanna use a winxp dualboot on a 70gig raptor,
so i have to care about my free diskspace.

i dont want to use hibernating!

so how big should my swap be?
it need much to fill up 8gig of ram- so if i give 2-4gig swap, it should be enough, should it?



second question is: how much space should i spend to home and root?

im in front of formating, so its a lil bit hurry ;)

---

### Post by vandorjw on 2009-04-04
I have 4GB of RAM and no swap.

I did not make a separate home partition. What I did do was make a separate DATA Partition, that windows and Ubuntu could both access, and where all my personal music etc would be stored.

Cheers - CC7

70 GB.
I would split that as such.

+/- 15 Ubuntu
+/- 25 Windows.
+/- 30 DATA

(PS: if you have another hard drive to store Music, documents etc, Split the 70 GB 50%)

---

### Post by wieman01 on 2009-04-04
Same size as your RAM. I suggest 8GB of SWAP.

---

### Post by apmcd47 on 2009-04-04
> **wieman01 said:**
> Same size as your RAM. I suggest 8GB of SWAP.

Ditto. Rule of thumb is swap is at least as large as RAM.

Andrew

---

### Post by derWalter on 2009-04-04
Ive got 250 500 and 500 gig harddisks for my data.

i need windows for adobe cs4 and lil bit of gaming. so i give 35 gig to windows.

8gig swap
10 root
17 home

i dont got experience with desktop linux systems, dont know how much is where stored. where programmes got installed and so on...

on my servers i got partitions for everything :)

---

### Post by vandorjw on 2009-04-04
Why 8GB of swap space?

People matched the amount of swap space with the amount of RAM they had available when Memory was an issue. (in case you ran a program, or two, that requires more memory that you have)

what program requires more than 8 GB of RAM??

I guess it doesn't really matter. If you run out of disk space on windows, you can always install programs on the other disks.

PS: I am quite certain that desktop Linux systems are structured similar to server installs.

---

### Post by derWalter on 2009-04-04
yes i think so too, but on my servers i got enough space for the mainsystem and strict limited programs. all data wich is generated, is stored in seperate partitions. if there is not enough space i expand the partition. all running in big arrays, so its complete different. i tried arch linux yeahrs ago, was quite fun, but not so easy to handle like XP. at the moment im migrating from vista64 ultimate to xp64 professional and set up a dual boot, because i want to switch to linux. only thing keeping me using windows is ADOBE... i hope i can switch to gimp inkscape and co.

photoshop fills 8 gig of ram and swapfiles! it works with uncompressed pixel data. if you got a big document in printresolution with hundreds of layers - there you go.
vista used 3,5 gig of ram at startup! so i ran out of ram very 
often... never mind, its history, fugging vista.

swap is used when ram is full AND for storing the whole ram when using hibernating. because of that you should have 2,5 times more swap then ram. as far as i can remember... hope linux spare my ram more than vista... 3,5gig on bootup... you know how much that is? ... xp uses 120mb at bootup... will c how kubuntu will perform :)

---

### Post by paxmark1 on 2009-04-04
I have 4 GB memory and 2 GB of swap with a dual core cpu and my swap is very very rarely used.  The old rules of thumb for swap are getting pretty old.  

Basically, how memory intensive are your planned programs in Linux.  

Multimedia editing?  

If not, two GB swap might be very well enough.  

peace mark

---

### Post by derWalter on 2009-04-04
yes, working heavy much with images. vector is no problem, but pixel work will cause heavy ram load. i think 4-8 gig are serious to not run out of space.

i am looking forward to a 200gig ssd raid array, then is space and swap no more problem :) - but it will take month till i got it, so i have to use my raptor as good as possible.

---

### Post by dandnsmith on 2009-04-04
> I have 4 GB memory and 2 GB of swap with a dual core cpu and my swap is very very rarely used. The old rules of thumb for swap are getting pretty old.

As far as I recall, the 'old' rules, read carefully, said as much swap as RAM, up to a max of 1GB. Since swap was devised as a way of making up for shortage of RAM, I think this is probably still good.

---

### Post by vandorjw on 2009-04-06
derWalter> i dont want to use hibernating! ......
swap is used when ram is full AND for storing the whole ram when using hibernating. because of that you should have 2,5 times more swap then ram.

Doesn't make sense to me...but then again..maybe you're right.
----
1GB swap max is reasonable. I guess it doesn't matter anymore now...
----
cheers - CC7

---

### Post by dandnsmith on 2009-04-06
> Doesn't make sense to me...but then again..maybe you're right.

Doesn't to me either - hiberfile.sys (or something like it) is where the hibernation stuff gets stored, swapfile.sys for the swap.

---

