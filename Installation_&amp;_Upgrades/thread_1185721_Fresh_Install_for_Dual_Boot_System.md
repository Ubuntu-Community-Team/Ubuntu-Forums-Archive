---
title: "Fresh Install for Dual Boot System"
date: 2009-06-12
forum: Installation &amp; Upgrades
---

### Post by Z47isthenew42 on 2009-06-12
I currently run a dual boot system using Windows Vista Ultimate and Ubuntu 8.04--The Hardy Heron.  I want to do a fresh install replacing my Ubuntu 8.04 with 9.04, but maintaining my Windows Vista Partition as I may go back to school and need Vista for some programs.  I have a CD that I ordered and was mailed to me.  I was wondering how exactly to do this.  I'm sorry if the question was answered already, but I tried searching and couldn't find any helpful posts.  Here a couple of screen shots that show what the partitions look like in both Vista's disk management tool and the Gparted that comes on the LiveCD of 9.04:

[[IMG]http://img261.imageshack.us/img261/2082/screenshotvista.th.jpg[/IMG]](http://img261.imageshack.us/i/screenshotvista.jpg/)

[[IMG]http://img208.imageshack.us/img208/1938/partitionsingparted.th.jpg[/IMG]](http://img208.imageshack.us/i/partitionsingparted.jpg/)

The second screen shot appears to be more clear.

---

### Post by merlinus on 2009-06-12
Boot from the cd, choose to install ubuntu, and when you get to the partitioning menu, select sda6 for / and sda7 for swap, and select to format sda6.

That would seem to be the easiest way to go.  It would overwrite your current installation.  But backup your data beforehand, as it will be lost if it currently resides on sda6.

Leave sda1, sda2, sda3, and sda5 alone.  DO NOT use them for anything or format them!

---

### Post by Z47isthenew42 on 2009-06-15
Thank you.  That sounds like it will work.

---

