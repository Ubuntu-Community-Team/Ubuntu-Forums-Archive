---
title: "Missing hard drive space after two ubuntu installs"
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by wvtalbot on 2009-08-01
I decided I wanted to play with ubuntu and set it up as a dual boot on my machine with vista.  After the first install, I notice there was zero extra space on the ubuntu partition so I deleted the partition in vista and fixed the mbr with recovery console.  Then I shrank the vista partition and tried again only to experience the same problem.  After doing this twice I now notice my hd is about 10GB short on total space, neither ubuntu installer or vista can find where this space went to.  Currently I have no ubuntu install on my machine, is there any program or way to recover the lost disk space in vista before I repartition and reinstall ubuntu? Also why is the ubuntu partitioner giving just enough space for the install and no extra room even when there is more available free space?

Thanks for helping a newbie out.

---

### Post by tommcd on 2009-08-01
> **wvtalbot said:**
> I decided I wanted to play with ubuntu and set it up as a dual boot on my machine with vista.  After the first install, I notice there was zero extra space on the ubuntu partition so I deleted the partition in vista and fixed the mbr with recovery console.  Then I shrank the vista partition and tried again only to experience the same problem.

How are you shrinking the Vista partition? Are you shrinking it in Vista, or are you using Ubuntu's partition tool?
> **wvtalbot said:**
> 
  ... my hd is about 10GB short on total space, neither ubuntu installer or vista can find where this space went to. ...is there any program or way to recover the lost disk space in vista before I repartition and reinstall ubuntu?
The partition tool that comes with vista should be able to do that. You probably have "free" or "unallocated" space on the drive after you deleted Ubuntu.
> **wvtalbot said:**
> 
 Also why is the ubuntu partitioner giving just enough space for the install and no extra room even when there is more available free space?

Try using manual partitioning when you install Ubuntu. Then shrink the Vista partition to the size you want. I would recommend shrinking Vista to free up 11GB of space, as long as you can spare it. Then create a 10GB root partition and a 1GB swap partition. Then proceed with the install. See this detailed guide. It uses as an example Jaunty + Windows 7; but it should be essentially the same for Vista:
[http://members.iinet.net.au/~herman546/p23.html](http://members.iinet.net.au/~herman546/p23.html)
Ignore the part about the dedicated grub partition in that tutorial. You don't need it.
Create the Ubuntu root partition using the ext3 filesystem.
Write back if you need more help.

And welcome to the Ubuntu forums!

---

