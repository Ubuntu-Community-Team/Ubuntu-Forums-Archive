---
title: "Need help recovering a Hard Drive"
date: 2008-08-11
forum: General Help
---

### Post by Biggerbean on 2008-08-11
Hi, I've read several threads on this but nothing I've tried seems to work...I'm wondering if running Ubuntu 8.04 is a wildly different version. 

Anyhow, here's the situation: I have an almost dead 3.5 inch drive on USB. It disappeared on a Mac when the power went out and it said, "Improper disconnecting a USB device. Some data loss may have occurred."  Massive understatement. The whole drive is gone.

Till I got it back to Ubuntu...which can see MOST of the file structure, but not all. I can copy some of the files but a bunch of the data has become corrupted.  There are definitely some large folders missing entirely.

The USB drive is /dev/sdb3 with directory /media/Bigger (the name of the drive) visible. There main drive I use has space to copy it, /dev/sda1 (directory= '/') and there's another drive on thesystem monitor, gvfs-fuse-daemon, with the exact same stats as the main 320GB drive (directory = "home/david/.gvfs")

I've tried to use dd_rescue and fsck to recover the drive but it always returns errors about not being get proper permissions, or, it starts and hangs after a 2 minutes and doesn't seem to do anything.

I'm trying sudo dd_rescue /dev/sdb3 /dev/sda1.   


I can't find a version of "testdisk" utility that runs on Ubuntu either.

I'm a total Ubuntu (and Linux) newbie...what the heck am I doing wrong and what can do, step by step, to recover the data files from this drive (fyi, it's just data, no OS crap to recover and just one partition.)

And if it does write something sucessfully, what do I do then?

Thanks for your help.

---

### Post by Biggerbean on 2008-08-11
Ok, I got it doing something...it's totally taking up my computing power...lots of screen activity...numbers and such moving...like 18457000k (after about 15 hours) does that mean it's 18MB into the 120GB drive??? Hope not. It also has 1.6% something in the corner. Can't be precise because I can't use that computer right now. 

So here's the question: It keeps flashing "Input/Output error"  and the drives space remaining is zero on a drive that had well over 120GB free to move stuff to. 

What gives? Can I stop it? Should I stop it. 

Help :(

---

### Post by Biggerbean on 2008-08-12
It's STILL chugging away. I'm not really sure what it's doing. One thing I noticed: the Harddrive light on my desktop is not flashing...meaning it's not writing the data? What the heck is it doing.  Is it safe to stop it? (How??) 

What to do? 

ANYONE???

---

### Post by Biggerbean on 2008-08-12
OK, here's what the dd_rescue screen looks like, repeating over and over again:

dd_rescue: (info):  ipos:  78124992.0k, opos:         78124992.0k, xferd:  78124992.0k
                    errs:      3251214, errxfer:           2641245.0k, succxfer:  78124992.0k
              +curr.rate:    30938kB/s, avg.rate:    42878kB/s, avg.load:  1.4%
dd_rescue: (info): /dev/sdb (78125000.0k): EOF
Summary for /dev/sdb3 -> input/output errors!
dd_rescue: (info): ipos:  78125000.0k, opos:         78125000.0k, xferd:  78125000.0k
                   errs:      3251229, errxfer:                2641252.0k, succxfer:  78125000.0k
             +curr.rate:    37037kB/s, avg.rate:    42878kB/s, avg.load:  1.4%


What does this even mean?

---

### Post by unutbu on 2008-08-12
Biggerbean, I'm sorry I don't know that much about dd_rescue, so I don't have any direct advice. However, you might find this page interesting:

[http://fedoraforum.org/forum/archive/index.php/t-129081.html](http://fedoraforum.org/forum/archive/index.php/t-129081.html)

---

