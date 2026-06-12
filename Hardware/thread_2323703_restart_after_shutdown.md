---
title: "restart after shutdown"
date: 2016-05-07
forum: Hardware
---

### Post by glyn2 on 2016-05-07
Hi I&#8217;m newto the Linux OS, I have installed Ubuntu 15.10 on a 240GB SSD with anadditional 3TB HDD for movies/tv series, my problem is when I shutdown, thesystem restarts, I think the cause is the 3TB HDD because when I found how tospin down the HDD (after 5min not in use) the system would reboot after the5min spin down time.
The 3TB HDDis from a windows 7 OS which had my movies/tv series on.
Ubuntu pickedup the HDD with all my movies/tv shows on ok, not sure if I needed to format inUbuntu, which I did not want to do as it is nearly full.
Any helpappreciated. 
 Thanks.

---

### Post by TheFu on 2016-05-08
Welcome to the forums.

Don't think spinning down a HDD (assume you used hdparm to set this) has anything to do with a system restarting.

To shutdown a system, I use "sudo shutdown -h now" in a terminal.  Does that work?  This will help determine if the problem is in the GUI somewhere or at a lower level.

How are you backing up all that media?  It is always best to use Unix-based file systems, unless there is a good reason not to do so.  HDDs always fail unexpectedly.  Imagine all that media is gone.  Inconvenience or major issue?  Use that as your guide to whether 1, 2, 3 backup copies are needed.

---

### Post by glyn2 on 2016-05-09
hi, thanks for replying, I tried your shutdown process and it did not work, the computer restarted. tried other shutdown processes from this forum, they also failed. 

I have my movies/TV files backed up on a NAS I just didn't want to format and recopy all the files unless absolutely necessary.

not sure what hdparm is.

---

### Post by TheFu on 2016-05-09
hdparm is the tool that controls hard drive settings - it is how you control sleep spin down. I don't know of any other method.

If that shutdown method didn't work - the issue is in the BIOS settings, 99.99999999% sure. Check there.

---

