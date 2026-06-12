---
title: "computer can't find the mount point"
date: 2010-05-05
forum: Hardware
---

### Post by tru infini on 2010-05-05
Last night everything was just fine with my new 1TB hard drive. I got it to automount so i wouldn't need root password to look at it. this morning when I log into my user name, it says that the mount point where My 1TB is supposed to be does not exist. My computer sees the hard drive but it wont mount as the mount point does not exist anymore. what would cause this and how cna i fix this? I just got done moving alot of sensitive data onto that hard drive and would not want to lose it all.
     Also when giving me commands of what to type in my terminal to fix this problem,...my ubuntu computer is NOT connected to the internet and I want to KEEP all the data currently on the new hard drive if possible. thank you

---

### Post by thebigob on 2010-05-05
Can you please post the results of running:

```

 sudo fdisk -l

```in a terminal with your external disk plugged in.

or you can take a screen shot of System -> Administration -> Disk Utility

---

### Post by tru infini on 2010-05-06
It's not an external disk. (at least it better not be) I think I have found the solution to this one problem but have gained several others. I upgraded to 10.04.

---

