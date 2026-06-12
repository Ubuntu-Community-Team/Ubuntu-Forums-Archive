---
title: "IDE raid with no raid controller, just typical IDE controller"
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by jeffhollon on 2008-02-28
anyone know how to do this.  i have ubuntu latest version, two 40Gb harddrives on a standard ide controller (each on seperate channel).  I know in windows you can do the dynamic thing, but i can't figure it out in ubuntu.  I have read all kinds of posts on dmraid, but everytime, no matter what i do i get No Raid Disks when i run the dmraid -r command.  I am kind of new to ubuntu so please forgive me if this is a bit underneath the vast majority.  I am just wanting to do raid0 for speed on this machine and that is all.  any help would be greatly appreciated.
is it even possible?


thanks,

Jeff

---

### Post by chrisdeckard on 2008-02-28
Read up on mdadm.

-Chris

---

### Post by jeffhollon on 2008-02-28
i have, doesn't help much.  i need some directed help.  this is what i am doing.  got the alternative desktop cd and go into setup and under partioning, go manual.  Set a primary on each disk for the full amount and set the type to raid.  when it ask me do i want to write this to the disk, i say yes and the screen goes blue and not much movement for at least ten minutes.  I restart the computer thinking it is locked up and the setup cd will not boot.  i have to disconnect one of the drives before i can get back into the cd setup, then i delete the partition and start again.  I have been doing this for a while now and about to give up.  I have read and followed the instructs i have found and nothing matches up and the same thing happens again and again.

---

### Post by chrisdeckard on 2008-02-28
It sounds like you have quite a hardware problem going on, but that wasn't evident in your original post.

Can you at least install Ubuntu on one drive, no RAID?  

-Chris

---

### Post by jeffhollon on 2008-02-28
i can get it installed after clearing the partitions, but i want to be able to mirror the discs.  right now, as i sit posting, i am at these steps.  

-both drives plugged in
-booted up alt install cd
-setup each drive as RAID AUTO Detect (or something like that)
-install asked me a couple of times if i wanted to do this, i said yes 
-screen is blue with a gray bar at the bottom
-the harddrive light is pretty steady for about 10 minutes now.
-not copying info just setting up before the actual install.
-no progress bar, but it is def doing something. 
-how long should i give this process before i say F-IT!!!!

any help would be great, i am about to loose my mind

thanks,

Jeff

---

