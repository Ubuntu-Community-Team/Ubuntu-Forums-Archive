---
title: "Using ubuntu to check for disk errors"
date: 2014-05-13
forum: Hardware
---

### Post by mecooper15 on 2014-05-13
Hey guys, 

Today I was running win7 and when I tried to turn my computer on it wouldn't boot. I used an ubuntu live disk to run a disk check, and my disk failed. The exact image that came up after I ran the test can be found here. 

[http://i.imgur.com/YwlFIkr.png](http://i.imgur.com/YwlFIkr.png)

I'm not very tech-savvy, but I'm assuming this means my harddrive is shot. My drive failed about six months ago, so my new one will be under warranty, but I just want to make sure that it is a drive failure before I send it back to the company. Can someone explain to me exactly what this means for my harddrive?

Thanks!

---

### Post by m-dw on 2014-05-13
The SMART self tests are not completely reliable, but as they are low-level hardware tests, it definitely looks like your HDD is fsck'd.   Were you able to mount the drive from the Ubuntu live CD?

I'm not sure what comes "installed" on the live DVD, but if it's there, you could try ntfsfix --no-action /dev/sda1 from a comand line to see if it recognises the file system and finds any errors.

---

### Post by Mark Phelps on 2014-05-13
Don't hold out hopes for ntfsfix to actually repair the filesystem on the drive; it can handle trivial errors at best -- it's not a substitute for Windows chkdsk.

If you have access to another PC, you can download the ISO image of the Minitool Partition Wizard Boot CD, burn that to CD, boot your PC from it -- and see if you can run the Check operation against your drive.  That runs Windows chkdsk.

---

### Post by m-dw on 2014-05-14
Yes, that's true, but if the meCooper15 doesn't have an alternative, ntfsfix --no-action will at least demonstrate whether the problem is a complete hardware failure making the disk unreadable or whether it is a filesystem issue that can be fixed.

---

