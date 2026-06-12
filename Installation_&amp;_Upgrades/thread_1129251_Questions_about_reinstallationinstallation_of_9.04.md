---
title: "Questions about reinstallation/installation of 9.04"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by Scarlath on 2009-04-18
Alright, so I'm having another try at Ubuntu once 9.04 is released. I already have Ubuntu installed (8.10, that is) on a second harddrive in my box. Now, the question is (the network does not work, else I'd update): How do I proceed?

Should I just remove the partitions and simply repartition the harddrive and then install? I do not need to save anything on the already installed version (I don't want to save anything as it didn't work properly, ...wireless network, last time - I haven't used it much - no files to save). Or should I just choose the already made partitions for the installation without having to do anything else?

I installed GRUB according to the default settings last time, should I just do this again to rewrite it?

That's all questions I got for now, thanks in advance. :)

---

### Post by vigyani on 2009-04-18
Does wired network work? You may have to download or borrow a Jaunty CD (live or alternate) from a friend.

I think it would be good idea to do a fresh install. You may decide to go for ext4 filesystem, as it is much faster.

I use the following partition table:

Swap 2.5 Gb
/ 20 GB
/home 60 GB
/home/user/archive 'rest of the space on HDD'

I usually do a fresh install on my system with the above partition scheme, without disturbing /home and archive (used for backup).

---

### Post by leonardo_neo on 2009-04-18
If you don't have any important document/setting to save, then I would recommend to do a fresh install.

If your internet is not working, then download the .iso image of Jaunty and burn it on some other computer.

Though many experienced users are reluctant for the new ext4 file system, I would like to recommend you that you should try that. It is fast. I have been using ext4 on Jaunty for a while, and I am happy with it's performance.

In your fresh install, you might want to have a separate /home partition, so that in your next upgrade, you won't have to lose your data and settings.

---

### Post by Scarlath on 2009-04-18
Thanks for the answers guys, I appreciate it. I've requested a CD of 9.04 (I'm in no hurry), so I'm fine on that part. 

When doing a fresh install though, do I delete the existing partitions and repartition the drive?

About Ext4, I've heard it's somewhat buggy (might have been because of the alpha/beta though?). Is this something I should not worry about though?

---

### Post by leonardo_neo on 2009-04-18
> **Scarlath said:**
> Thanks for the answers guys, I appreciate it. I've requested a CD of 9.04 (I'm in no hurry), so I'm fine on that part. 

When doing a fresh install though, do I delete the existing partitions and repartition the drive?

About Ext4, I've heard it's somewhat buggy (might have been because of the alpha/beta though?). Is this something I should not worry about though?

Well if you already have a separate /home partition, then you can delete and formate the existing ext3 partition, and install the newer version on that. 

But as you have said that you don't have any important files to carry forward, so I think you should delete everything and start fresh. 

Yes you have heard right about ext4 that it is somewhat buggy presently. To know the issues of ext4, read the following link....

[http://www.h-online.com/open/Ext4-data-loss-explanations-and-workarounds--/news/112892]("http://www.h-online.com/open/Ext4-data-loss-explanations-and-workarounds--/news/112892")

But I am using ext4 presently, and I never had similar problem. If you wish to use your comp for creating important documents, then go with ext3 only. If you wish to use your comp for general purpose (browsing and things) then go with ext4.

---

