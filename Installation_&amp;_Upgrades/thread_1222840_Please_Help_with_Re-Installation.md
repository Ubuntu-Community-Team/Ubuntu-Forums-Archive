---
title: "Please Help with Re-Installation"
date: 2009-07-25
forum: Installation &amp; Upgrades
---

### Post by brett- on 2009-07-25
Greetings,

This should be a simple question.  When I originally set up my Linux computer I partitioned the hard drive as follows - 

/dev/sda1 ext3 /boot
/dev/sda2 ext /
/dev/sda3 linux-swap
/dev/sda4 ext3 /home

I started with 8.04, upgraded to 8.1 and then upgraded to 9.04.  I am having stability problems with 9.04 and want to go back to 8.1 for now.

How do I reinstall and preserve /home?  :confused:  This question may have been covered in another post but I can't find it.

---

### Post by 67GTA on 2009-07-25
When you start the installer, choose the manual partition option. When you edit the /home partition, tell it to mount it as /home, but NOT to format it. It will simply be mounted as /home after the new install and your data will not be touched.

---

### Post by brett- on 2009-07-25
Okay, that makes sense, thanks alot.  I did not notice those options during the initial installation.  It sounds as if that will preserve email and virtual machines?

---

### Post by 67GTA on 2009-07-25
None of the data will be touched if it is not formatted. It will only be marked as your /home partition for the new install. Everything will be just as it is now. It will be like you never left home :D If a partition is formatted, all the data is wiped, and a new file system is setup.

---

### Post by presence1960 on 2009-07-25
hopefully your /home is still ext 3. if you converted it to ext 4 you are going to have a problem because ext 3 can't access ext 4 partitions. If you made /home ext 4 on 9.04 then back it up and during the install select that partition, set it to ext3 filesystem, check format box and set mountpoint  as /home. if you left /home as ext 3 in 9.04 you are in great shape, do as 67GTA says to do. After the install move your data back to /home.

---

### Post by brett- on 2009-07-25
Good point there.  Since I got to where I am (9.04) by way of updates, no reformat was done.  If I leave my machine on for a few hours I get a blank screen in 9.04.  Frustrating because when it's running, it runs good.  I could not nail down a common cause through the forums.  It will probably wind up being my hard drive!

---

### Post by presence1960 on 2009-07-25
if you got to 9.04 via dist upgrade your /home is probably ext 3 still. As for the blank screen check your screen saver settings- one of the options is a blank screen.

---

### Post by PhoHammer on 2009-07-26
> **presence1960 said:**
>  As for the blank screen check your screen saver settings- one of the options is a blank screen.

Hopefully you tried an input (i.e. move your mouse or hit a key) to see if it was merely a
screen saver...?

---

### Post by brett- on 2009-07-26
I checked all of that by disabling screen saver and display sleep mode in power management and AMD "cool and quite" about a month ago.  Even enabled ctrl-alt-backspace to restart X, no luck.  Case is well ventilated and temperatures are normal.  When the screen goes dark, the only way I have found to recover is a boot.  Quite often applications will have black areas after maximizing or during scrolling;  at that point I know a freeze out is coming!  Has anyone ever seen that?  It is tempting to think it is hardware related but this started immediately after upgrading to 9.04.  One thing that seemed to help (now I am getting subjective) was to dump fglxr and use the open source display package.  I don't know at this point.  I am glad to learn how to reinstall while retaining home but I wish I could solve this stability problem.

---

### Post by brett- on 2009-08-30
A quick follow up to this post.  I did re-install Ubuntu rolling back from 9.04 AMD64 to 8.10 i386 (what a relief).  It was very simple and fast.  I did not get a chance to back up any settings.  As it turned out, not a problem.  All software re-installed (Firefox, Evolution, Crossover, Virtual Box, Amarok etc.) retained all data and settings.  Lesson learned - always have a separate partition for /home!

:guitar:

---

