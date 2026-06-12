---
title: "Install Partitioner Does Not Work"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by scoon2231 on 2009-08-22
I have wasted over 10 hours attempting to begin an Utuntu install from CD.  Version 9.04.  I need to install on an external HD, and the only option available for that is to perform a Manual Partition.

Once I am presented with a list of hard drives I choose the external HD.  I then choose New Partition Table.  I select Continue from the dialog box that pops up.  After I do that the screen flashes for less than 1 second, and starts over.

I have repeated this at least 50 times, with the same result. I do not get the page to create a new Partition Table.

I have tried rebooting from CD and I get the same result.

I have created a new Ubuntu CD and I get the same result.

i have done the CD check and it shows that the CD is good.

I have checked memory and it checks out OK.

There are absolutely no error messages of any kind. The screen flashes for less than 1 second and puts me back to the start of the partitioning exercise.

At this point I am completely fed up with Ubuntu install.  What is going on?

Thanks.

---

### Post by zkriesse on 2009-08-22
Well you would probably have to install Ubuntu on the pc hd before trying to setup an external hd.

---

### Post by Bartender on 2009-08-23
I don't partition from the Ubuntu CD.  I always partition using a GParted LiveCD.  

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

From this page you navigate to the latest stable version, download the .iso, make a CD out of it just like the Ubuntu LiveCD.

Burn it slow, use good quality media, use a CD-R, not RW...

When you're done you have a stand-alone partitioner.  I don't know the in's and out's of this exactly, but it just works more reliably than the partitioner on the Ubuntu CD, even though it's basically the same utility.

Oh, something else.  It's easy to look up older versions of GParted from SourceForge.  I have a 2 year old GParted LiveCD that sometimes works when the newer one doesn't.  The older one doesn't let me format to ext4 of course...

Another option - can you pop the HDD out of the external and plug it directly into your PC?

Maybe there's something in the external's circuit board, something in the way it identifies itself to the PC, that's causing the error (?)  :-k

---

