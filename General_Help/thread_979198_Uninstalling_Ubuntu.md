---
title: "Uninstalling Ubuntu"
date: 2008-11-11
forum: General Help
---

### Post by cloroxmartini on 2008-11-11
Alright, first off, I'm not unhappy with Ubuntu.  But recently there have been a lot of bugs and I was wondering how I could just uninstall the OS and give back the disk space to Windows (since I am dual booting).  How can I do this?

---

### Post by Bobby Rankin on 2008-11-11
Insert the CD you used to install Ubuntu originally, and boot into it. When it boots, go to Applications -> Accessories -> Terminal. Type

```
sudo gparted
```

and a partitioning menu will come up.

I don't know how experienced you are, but if your not experienced -- don't get scared. This won't be hard.

In the second column, you will see the filesystem type. Delete any partition that has a filesystem type of "ext2," "ext3," or "swap". Then, there should be one partition remaining. Right click on this partition, choose resize, and drag the size choice the farthest that it can go. Now, at the top of the program, click on "Apply".

**IMPORTANT: You need to change your boot loader as well to make sure that it boots windows instead of Ubuntu.** Find out how to do that here: [http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/](http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/)

Good luck! Sorry to hear that the bugs got to you.
:) Bobby

---

### Post by Mr_JMM on 2008-11-11
Before you do, if you're willing to give it one more go and you have dived straight into Intrepid (8.10), I recommend trying hardy (8.04). You might find it much more stable and less buggy.

---

### Post by cloroxmartini on 2008-11-11
Hardy is actually what I've been running.  But for some reason I downloaded some updates and it got buggy for some reason.  Besides, I think I'm going to try and try installing it on a different machine.

---

### Post by cloroxmartini on 2008-11-12
So I got into gparted but I can only delete the partition with extension ext3.  There is a swap partition which I cannot delete.  There is an icon that looks like a pair of keys next to it which I assume means that it's locked or something like that.  So this is my dilemma as of this moment.

---

### Post by plucky on 2008-11-12
> **cloroxmartini said:**
> So I got into gparted but I can only delete the partition with extension ext3.  There is a swap partition which I cannot delete.  There is an icon that looks like a pair of keys next to it which I assume means that it's locked or something like that.  So this is my dilemma as of this moment.

Select the partition,right click and select swapoff.The keys means the partition is mounted,so you have to turn off swap to be able to delete the partition.


Good Luck

---

### Post by bodhi.zazen on 2008-11-12
> **cloroxmartini said:**
> Alright, first off, I'm not unhappy with Ubuntu.  But recently there have been a lot of bugs and I was wondering how I could just uninstall the OS and give back the disk space to Windows (since I am dual booting).  How can I do this?

Follow this how to :

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

You may delete the Ubuntu partitions and give the space back to windows, but you have to restore the windows boot loader (if you simply delete Ubuntu you will not be able to easily boot windows).

---

