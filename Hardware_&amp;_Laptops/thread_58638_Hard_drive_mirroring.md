---
title: "Hard drive mirroring?"
date: 2005-08-21
forum: Hardware &amp; Laptops
---

### Post by Ricapar on 2005-08-21
Right now I'm using a 20GB hard drive. Everything works fine, but I do find myself low on space quite often. I don't like having less than 1GB free.

A friend gave me a 30GB that he didn't need anymore, but works.
I'm wondering how would I go about making an exact copy of my current 20GB to this 30GB.

I know it's not that much of an increase in space, but 10 gigs is a lot for me :-|

---

### Post by nad on 2005-08-21
First, get yourself a live cd (knoppix, ubuntu, etc). You will run from the cd with both drives installed in your system.

You could now use the dd command to make an exact copy. You will not need to play with grub as your entire drive will be copied bit for bit. dd bs=32768 if=/dev/drive_to_copy_from of=/dev/drive_to_copy_to . Note that these are drive designations, not partitions. You will then need to use parted to resize the new partition and filesystem (remember, dd makes an exact copy).

You could also partition and format the new drive, then copy your data over: cp -dpR /dev/hda1/* /dev/hdb1/. (yes, that is a dot after the slash). But now you have to install grub to your new drive.

How about simply installing both drives, and once you have partitioned and made your filesystem, move /home and /var to your new drive (or some other configuration)? No headaches, no hassles (unless that 20 gig is destined for someone else).

---

### Post by Ricapar on 2005-08-21
Thanks. I'll try that.

And I would use both drives, but as you guessed, the current hard drive is going to someone else. She currently only has 10 gigs, running Windows XP and wants to give Ubuntu a try.

---

### Post by nad on 2005-08-21
Another piece of advice: This copying could take a while. Thirty minutes to an hour. Be patient.

If you use the dd command, from another terminal window you can send dd a SIGUSR1 to check the status. First you need the PID of the running dd process: ps -C dd . Now: kill -USR1 $pid  to see the status. The dd man page has an example that will update every second. You do not want to do this as it will slow down the copying.

---

