---
title: "[SOLVED] Please Help! Partition Showing 25GB of Wrong Disk Usage"
date: 2008-08-22
forum: General Help
---

### Post by ragflan on 2008-08-22
Hi. I'm under Hardy Heron. I just used a GParted Live CD and I did these steps:

1.) Resize SDA1 from 80gb to 40gb.
2.) Resize SDA2 from 10gb to 25gb using empty space.
3.) Resize SDA4 from 20gb to 45gb using empty space.

My **SDA4 is my /home** mount point. Thing is, the partitioning was successful when I joined the empty space to SDA2, and the disk space is correct. 

But I **added 25gb of empty space to my /home** mount point. After a long time, the **partitioning failed**.  I** logged off the live CD and logged in normally** and the **25gb is coming out as Used space**!

Please help! **First screenshot is before** I changed anything. And **second one is after.** 

[IMG]http://ramipage.googlepages.com/Screenshot--dev-sda-GParted.png[/IMG]

[IMG]http://ramipage.googlepages.com/Screenshot--dev-sda-GPartedasd.png[/IMG]

---

### Post by puppywhacker on 2008-08-22
I don't know where the partitioning actually failed, but it sounds like during the resizing of SDA4 your /home partition. Save the 4Gb of data that was there (fits on a DVD-ROM) and reformat the space so that it is empty and clean.

It looks like the partition got bigger but the filesystem ext3 didn't grow much inside the space it has now. You might give resizing another shot, but it is always a bit risky, so make backups while you can.

EDIT: data from /home ofcourse also fits nicely into your root partition SDA2

---

### Post by ragflan on 2008-08-22
I put the live CD back in and booted into it. I started GParted and asked it to check for errors on the partition /home. It took about 2 minutes, and then now it's correct! It recovered back the 25GB and put it in my /home partition. It's all fixed! Haha! Happy!

---

