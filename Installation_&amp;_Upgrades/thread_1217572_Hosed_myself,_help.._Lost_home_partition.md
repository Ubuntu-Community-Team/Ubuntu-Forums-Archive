---
title: "Hosed myself, help.. Lost home partition"
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by ishmael2k on 2009-07-19
I did something I once vowed never to do. I changed my setup in 9.04 w/o a backup. 

I wanted a separate home partition and used [this]("http://www.psychocats.net/ubuntu/separatehome") to try and set it up. When I got to the final instructions (gksudo gedit /old/etc/fstab) on directing ubuntu to use the new home part. I got an error stating that I could not access/edit fstab.?? 

Needless to say it failed on me at that point and now I can't log into that pc. Tells me my home directory is listed at home/username but does not seem to exist. 

I have tried using the helps on that page to no avail. Tried recovery mode on the live cd, also with no luck. Any suggestions? I have searched here and online and will continue to do so. 

Let me know what other info you need.

---

### Post by ugm6hr on 2009-07-19
Consider using a LiveCD to backup your files at this stage.

The original partition should contain the /old/home_backup directory, which you should be able to recover.

Then, if all else fails, just reinstall.

---

### Post by ishmael2k on 2009-07-19
I was just starting to type a followup when I decided to at the thread. 

I did find the back-up file, it is located in the home_backup folder. 

So I can save them, now how do I recover the partition? 

Will continue to look. 

Thanks!

---

### Post by ugm6hr on 2009-07-19
> **ishmael2k said:**
> So I can save them, now how do I recover the partition? 

Don't know.

I suspect it will actually be quicker to reinstall fresh.  Create a new partition for /home at that stage and be done with it.

It's easier than moving to a separate partition after the fact.

---

### Post by ishmael2k on 2009-07-20
Well I did it... No I didn't save the partition but I did save my files. Re-loaded 9.04 and set the partitions the way I want. 

I now have :

/swap 2.5g
/ 50g
/home 197g

Now I am getting it all working friendly again.

Thanks!:o

---

