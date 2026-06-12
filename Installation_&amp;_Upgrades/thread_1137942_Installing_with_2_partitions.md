---
title: "Installing with 2 partitions"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by jamesdcarroll on 2009-04-26
I have two drives in my system and the one that has my original 8.10 install is not working well; I/O buffer errors and other nasty things.  One of the suggestions was to 'dd' it to another partition before trying to recover it. So I was going to install 8.10 to my other drive and partition it into two partitions so that I can do so.

When I get to the 'manual partition' page of the install, I set the sizes that I wanted, but the dialog demanded that I choose a mountpoint for both. For the one at the front of the disk '/' seems to make sense, but for the second one I don't know what to put. 

Any insights would be greatly appreciated.

Thanks

---

### Post by alphacrucis2 on 2009-04-26
> **jamesdcarroll said:**
> I have two drives in my system and the one that has my original 8.10 install is not working well; I/O buffer errors and other nasty things.  One of the suggestions was to 'dd' it to another partition before trying to recover it. So I was going to install 8.10 to my other drive and partition it into two partitions so that I can do so.

When I get to the 'manual partition' page of the install, I set the sizes that I wanted, but the dialog demanded that I choose a mountpoint for both. For the one at the front of the disk '/' seems to make sense, but for the second one I don't know what to put. 

Any insights would be greatly appreciated.

Thanks

The mount point is where, in the file system directory structure, that the mounted file system appears. For example if you set the mount point to /home then the data in that partition will appear to be under the directory /home.

---

### Post by jamesdcarroll on 2009-04-26
Will that therefore 'overide' the default location of /home (which would be the first partition, right)?  Or would /home be split with part of it on one partition and one on the other? I've not done this before and in all honesty I tend to put EVERYTHING in my /home/jim folder since the linux filesystem just eludes me for some reason. How would I know what was on which partition?

Thanks,

---

