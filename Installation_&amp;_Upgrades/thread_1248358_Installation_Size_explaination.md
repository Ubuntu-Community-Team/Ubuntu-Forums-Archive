---
title: "Installation Size explaination"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by orsenthil on 2009-08-24
The Wubi installation prompts to select the Installation Size during the Install time.
I had used wubi 8.04 and it had installation size I think upto 10GB or 15 GB ( I am not sure),  but more recently I helped a friend and I noticed that the installation size gave option for 30, 40, 60 GB.

I retried to locate information on what exactly is this Installation Size about and I am unable to find any concrete references.  

**What is this Installation Size all about? Why does it matter and what would be a good selection?**  
I think, this can make it to FAQ or Support questions of Wubi guide.

Based on the material I found over the web, my understanding is as Wubi works on the principle of installing Ubuntu as a file, this is the file-size we give to the Ubuntu Install. 
This is like the Complete Size of the Hard-disk that Ubuntu can size from within. Am I correct in my understanding?

Now, if I try store more than the file-size, it would give No Space in the Disk, correct?
And for that, Wubi Guide provides [help in expanding]("https://wiki.ubuntu.com/WubiGuide#How%20big%20should%20the%20the%20virtual%20disks%20be?") the disk size..

Please point out if I have missed anything.

I have the following Additional questions too. 

1) What should be the disk-size as reported by **du -sh /**, when done from Ubuntu installed using wubi? Should it give the installation size initially selected during the install?

2) If 1 is true, then where is the **/host **size accounted? If /host is also included then the complete HDD size should be available under /. Isn't it?

---

### Post by presence1960 on 2009-08-24
when you install via wubi you are creating a file within your Windows filesystem which will be Ubuntu's home. 

When choosing an installation size you are saying allow Ubuntu that much room within the windows filesystem. That is why there are options to choose, someone may not be able to allot 80 Gb for Ubuntu but may be able to allot say 10 or 15 GB.

Installing via wubi is not meant to be a permanent solution. it is meant to be a way to test drive Ubuntu to see if you like it without making changes to your hard disk. if you like Ubuntu and want to use it I recommend partitioning your hard disk and dual booting windows/Ubuntu.

Another note- wubi installs experience performance degradation to to windows file system fragmentation. remember your Ubuntu "install" is actually a file in the windows file system.

Doubt this? see [here]("https://help.ubuntu.com/community/Wubi")

---

