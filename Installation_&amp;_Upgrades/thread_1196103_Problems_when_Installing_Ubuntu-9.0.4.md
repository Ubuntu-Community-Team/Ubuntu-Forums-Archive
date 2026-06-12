---
title: "Problems when Installing Ubuntu-9.0.4"
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by Matuka on 2009-06-24
Hello,
I've been rather keen into trying out Ubuntu for a little while now, and since then I have remained in either Windows or in the Ubuntu Live Test...

But since I previously formatted my HDD into two separate locations for Windows XP and Windows 7, I've also got around 20gb left of which I'm thinking of installing Ubuntu on...

But here's the problem, when ever I'm at the Partitioning screen I choose advance and then I go to the reaming space and create a new partition out of it, I set it to a Logical Type with the Fat-32 Format, Also the Location for the New Partition is "At the Begining", and not only that the Mount is set as "/Boot".

Now after all of this is done -- I go to "Forward" and it comes up with the same error over and over again... Of which I have a screen-shot of:

[IMG]http://www.cubeupload.com/files/805800untitled.png[/IMG]
(Note. I used Gimp to edit it a little, thank goodness that the same controls in Gimp pretty much Remain, :D).

Could I get any assistance?

Thanks in advance,

EDIT:
Also to avoid trolling or flaming -- I've tried a search via Google on this matter and no prevail sad to say...
And yes I did sign up in order to ask this question... :D

[FONT=Arial Black][SIZE=7]_**EDIT2: problem is solved! Woot!**_[/SIZE][/FONT] <3 The quick Community...

---

### Post by mk1w86 on 2009-06-24
There is a thread here on how to set up your partitions for Ubuntu

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

Basically you need a root partition mounted on / and a swap partition which is similar to virtual memory in Windows.

---

### Post by merlinus on 2009-06-24
You need to set format to ext3.  linux does not run on fat nor ntfs.  After doing this, you usually can right-click on the partition and select the mountpoint -- / (or root).

---

### Post by mk1w86 on 2009-06-24
This explains the partitions more simply

[https://help.ubuntu.com/9.04/installation-guide/powerpc/partition-sizing.html](https://help.ubuntu.com/9.04/installation-guide/powerpc/partition-sizing.html)

---

### Post by hunterGT on 2009-06-24
I've had this happen to me while creating several partitions. The cure was to make sure one of the partitions was mounted to /root. But there may be another way, because I never had to do that before.

---

### Post by presence1960 on 2009-06-24
You want to create a swap partition first from that free space. I would recommend 1 to 1.5 times your RAM if you want to use suspend and/or hibernate.
When you get to the Prepare disk space window of the partitioner select manual option (see attached pic). Then highlight that free space for root and click Edit Partition. Set partition type to Primary or Logical, set Use as (Filesystem) to ext 3 or ext 4. Then set Mountpoint to /. Highlight intended swap partition and set Use as to swap. Then proceed with the install.

---

### Post by Matuka on 2009-06-24
Hey there guys, thank you for the incredibly fast replies (Usually on forums it'll take at-least 30 minutes for someone to even look at the thread)... Anyhow, I've got the problem sorted out thanks to your help!

Currently I am using EXT4 with a mount of "/"(Just that)...

And it let me pass onto Stage 5...

Also thank you [mk1w86]("http://ubuntuforums.org/member.php?u=531844") for the two(Or more) topics on partitions in linux/ubuntu -- There actually very use-full and contain much knowledge(made myself a mental note to Bookmark them where Ubuntu is finally finished installing).

Also thank you [presence1960]("http://ubuntuforums.org/member.php?u=657448") for the easy guide on what I should of done... :) Fixed up all the problems I had...

Thank you all very much,

EDIT: Also [merlinus]("http://ubuntuforums.org/member.php?u=277749"), if Fat isn't supported than why are both Fat-16 and Fat-32 listed? I'm going to take a wild guess and say it's because the Ubuntu Partitioner also allows you to partition your HDD for other operating systems such as Windows or Macintosh(Although im unaware if their is such as thing as a Mac Install CD, as most, or all Mac units come with it installed).

---

### Post by presence1960 on 2009-06-24
> **Matuka said:**
> Hey there guys, thank you for the incredibly fast replies (Usually on forums it'll take at-least 30 minutes for someone to even look at the thread)... Anyhow, I've got the problem sorted out thanks to your help!

Currently I am using EXT4 with a mount of "/"(Just that)...

And it let me pass onto Stage 5...

Also thank you [mk1w86]("http://ubuntuforums.org/member.php?u=531844") for the two(Or more) topics on partitions in linux/ubuntu -- There actualy very use-full and contain much knowledge(made myself a mental note to Bookmark them where Ubuntu is finally finished installing).

Also thank you [presence1960]("http://ubuntuforums.org/member.php?u=657448") for the easy guide on what I should've done... :) Fixed up all the problems I had...

Thank you all very much,

That's what I am talking about! Enjoy Ubuntu.

---

### Post by Matuka on 2009-06-24
> **presence1960 said:**
> That's what I am talking about! Enjoy Ubuntu.
I know I most certainly will! :) The power of it is far more superior than of which Windows 7 uses -- And even in the 32bit live it's still amazingly fast and quick...

*Jumps on and ride the Ubuntu fan boy/girl train* :)

---

### Post by merlinus on 2009-06-24
> 
EDIT: Also [merlinus]("http://ubuntuforums.org/member.php?u=277749"), if Fat isn't supported than why are both Fat-16 and Fat-32 listed? I'm going to take a wild guess and say it's because the Ubuntu Partitioner also allows you to partition your HDD for other operating systems such as Windows or Macintosh(Although im unaware if their is such as thing as a Mac Install CD, as most, or all Mac units come with it installed).


You are correct.  Often during installation someone may wish to create a partition for sharing data between windows and ubuntu, so that's why there are other formatting choices besides those used for linux.

---

### Post by mk1w86 on 2009-06-24
> [QUOTE]Quote:
EDIT: Also merlinus, if Fat isn't supported than why are both Fat-16 and Fat-32 listed? I'm going to take a wild guess and say it's because the Ubuntu Partitioner also allows you to partition your HDD for other operating systems such as Windows or Macintosh(Although im unaware if their is such as thing as a Mac Install CD, as most, or all Mac units come with it installed).
You are correct. Often during installation someone may wish to create a partition for sharing data between windows and ubuntu, so that's why there are other formatting choices besides those used for linux.[/QUOTE]

You can install Ubuntu on a FAT32 partition if you are installing to a USB flash drive for example.

---

### Post by merlinus on 2009-06-24
So linux runs on fat32?  I find this very hard to believe, but of course I can be totally mistaken.

---

### Post by presence1960 on 2009-06-24
> **merlinus said:**
> So linux runs on fat32?  I find this very hard to believe, but of course I can be totally mistaken.

My Jaunty Live CD I created on a USB drive is formatted in FAT 32. That is the Live CD on USB drive. I seriously doubt whether a full installation to FAT32 is possible.

Those other filesystem options are there because Partition Editor (gparted) on the Live CD and  gparted Live CD will boot and partition any machine no matter what is on the partitions.

---

### Post by mk1w86 on 2009-06-24
> So linux runs on fat32? I find this very hard to believe, but of course I can be totally mistaken.

Yes but I would not usually recommend it for obvious reasons apart from maybe the above scenario where USB flash drives are not usually very large.

---

### Post by philcamlin on 2009-06-24
use the whole disk :popcorn:

---

### Post by Matuka on 2009-06-24
> **philcamlin said:**
> use the whole disk :popcorn:
The previous problem has been solved my friend, :) Also I am not going to use a full disc for Linux as I am more or less a Windows user and I should remain like that for 75% of my life-time as I do game development/Modifications and photography - And if the Game that I'm developing for has problems running under any type of Windows application Emulator, then I'll have to resort to using Windows.

---

