---
title: "n00bie help"
date: 2008-08-25
forum: General Help
---

### Post by Klingz on 2008-08-25
Hey,

-I'm not quite sure if this is the right forum for this, please redirect me to the right if not so.

I've finely cleaned my desktop for some "rabbits" and decided to install Ubuntu (v8.04.1). Thoe I've had v7.0something installed but never got to use it properly due to all thoes rabbits inside. Two more months and they would have been ready to begin at school... :lolflag:

First I want to state that I'm "all into" Windows... Thoe I'm hoping to do something about that :) I allso know that in Linux-terms, using Windows-terms in a Linux environment is allmost like swearing in church. So I hope you can forgive me for my lack of knowledge.

My plans is as I have 2 hdds on 74.53 GB (80.000 MB) and hoping to have a most optimaised system as my "power" on my lady aint "-08" but more -02.

In Windows terms this would be like having the main system on HDD0 and a own Swap-Partion on HDD1.
HDD0PRT0 should have all users and programs, except big games (like Eve-Online with 6 GB as one of the "Minimum Requirements") whish I want on my second partion on HDD0 (or maybe HDD1 if this is to prefer).
On HDD1 I'm thinking about making the first 4GB to a Swap-partion. The rest I had plans to splin in two new partions for datastore.

Would this be a good setup or should I do something different?

Furthermore, this with '/', '/boot', '/home', '/tmp', '/usr', '/var', '/srv', '/opt' and '/usr/local' I got problems finding information about how and where to use them, so if you could give me some introduction to there use or some links where to info is. I see that this "point" can be one "big" one some I'm more then happy with some refferenses or links to them.

And to last, whish filesystem should I use on the different partionses?

Kindly reagard
Klingz

---

### Post by Mgiacchetti on 2008-08-25
well "/" and "/home" on different partitions is more likely to be the setup that most people use. (you will notice that "/" is the root of the drive, with /tmp /usr /var etc under it.
These you can use ext3 filesystem


If your system is older than an ipod, (or a usb stick for that matter) you may wish to place /boot at the first few sectors of the disk, then / ,  then swap, then /home. because of the bios limitation that may be present.

I'm not exactly sure if the above is 100% correct (pertaining to the /boot section of the post) and i'm sure someone else would be glad to correct me or back me up depending on the accuracy of it.

---

### Post by mike2357 on 2008-08-25
Don't worry about whether using Windows terminology is like swearing in church; it's all you know at this point and many of the Windows terms do in fact have Linux equivalents.

For the size of the system you're talking about, I suggest that you not worry about which file systems are going to be on what partition, and how much to allocate to swap, etc.  You can just let Ubuntu's installation CD figure out the size of the swap, and allow the entire installation to be in just one partition.  To be sure there are some reasons why you may not want to do this, but since you're just starting out I think it's more important to jump in and start using Linux and learning.  Different directories, such as /etc, /home, /usr, /etc can be all on the same file system.  Incidentally, I've only had one file system for Linux for several years and I've never run into any problems.

You can enter "unix file systems" in your favorite search engine, and you will find plenty of listings that explain what /etc, /home, /var etc. are for.  You might also take a look at this link:

[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows]("https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows")

There are plenty of Linux guides in bookstores, and if you're like me, sometimes there's no substitute for seeing something on paper.  So I'd suggest picking one up that looks like it addresses most of your questions.

---

