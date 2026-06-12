---
title: "[SOLVED] Best way to give Linux a bigger partition?"
date: 2008-10-05
forum: General Help
---

### Post by chenguo4 on 2008-10-05
So I installed Ubuntu (dualboot with XP) for a class. I figured I'd only use it for the class, and gave it 8gb out of 100. 

But now that I've been using Linux for a while, I find I like it a lot better than Windows, once everything's been properly set up.

So my question is, is there a way to give more of my 100gb HD to Linux without wiping everything and starting over? I wanna shoot for something like minimum needed + 10gb for Windows, rest for Linux.

Thanks in advance.

---

### Post by Idefix82 on 2008-10-05
You can use GParted, which is on the LiveCD, to resize partitions. You will have to boot from the LiveCD since you can resize a currently mounted partition.
You may also think about creating several partitions for Ubuntu, like a separate one for /home (probably reasonably large) and a small one for /boot (about 100 MB, 200 to be on the absolutely safe side) to increase stability and to facilitate upgrades.

---

### Post by chenguo4 on 2008-10-05
Wow thanks for the fast response. I'll get right to it. 

I'm not familiar with Linux yet so the multiple partitioning might have to wait, as I'd have no idea what partitions need what. Just out of curiosity though, how would this increase stability?

---

### Post by Idefix82 on 2008-10-05
For example if the folder /boot sits in its own partition then it will be pretty hard to destroy by a bad installation of software or by a mistake on your part. Thus you will always be able to boot even if most of the rest of the system get destroyed (not that this is likely to happen).
Also, if /home is in its own partition then it will be easier to upgrade to the next version of Ubuntu since you will be able to tell it to use the old /home folder. So you will get a new system but keep your settings, Photos, Music, whatnot.

For more thoughts about partitioning you can have a look at some ideas I was giving to another person in this thread:
[http://ubuntuforums.org/showthread.php?t=928600&page=2]("http://ubuntuforums.org/showthread.php?t=928600&page=2")
It's in my first two posts on that page. But don't worry about it too much if you are not fussed about having a "perfect" setup. A separate /home partition is handy for the above reason (and for another one given in the link), everything else is a bonus.

---

### Post by chenguo4 on 2008-10-05
Thanks a bunch! Very interesting read, sadly I'll probably have to wait til winter break to try this out, but it's definitely on my todo list now.

---

### Post by chenguo4 on 2008-10-06
Ok so I just tried this, and problem... I decreased the Windows partition, but it wont let me increase the Linux partition? Does this have anything to do with the former Windows partition being NTFS?

Apparently it wont let me reformat that unallocated space, nor can I make a new partition out of it (already have 4 partitions, windowns, linux, recovery, and something that I have no clue about). Is there a way to reformat that unallocated NTFS to Linux (which I think is ext3?)

edit: nvm... I was trying to resize a subpartition instead of the actual Linux partition.

---

### Post by Idefix82 on 2008-10-06
I hope it's not too late but when resizing partitions it's best to do one step at a time and boot into Ubuntu after every step. This way you are making sure you don't mess up the existing installs completely and if something goes wrong you will know exactly which step caused the problem so it will be easier to repair.

---

