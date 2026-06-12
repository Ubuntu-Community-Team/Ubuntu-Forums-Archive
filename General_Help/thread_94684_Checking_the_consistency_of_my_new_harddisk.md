---
title: "Checking the consistency of my new harddisk"
date: 2005-11-24
forum: General Help
---

### Post by daller on 2005-11-24
Hi There,

Just got a new harddisk for my computer, but I would like to check the consistency of it (dpkg reports about storage segment faults - Freely translated from danish)

I understand that I can use e2fsck ??? - But the drive is mounted!

...How do I check it?

Please tell me that Dapper has NOTHING to do with this!

---

### Post by poptones on 2005-11-24
It contains many files? How is it formatted? ext3?

Is it your goal to test the drive or the file system? does the drive sometimes hang or is the system slow to respond, or did you just start getting errors after a bad shutdown?

To do a basic test just unmount it by doing "sudo su" 

enter fuser -k /dev/{your drive} to make sure there are no open files
umount /dev/{yourdrive} to unmount it
fsck /dev/{yourdrive} to test it. 

If the drive is really new you probably got a bad one and need to perform a more in depth diagnostic. 

first thing is to try backing up your stuff. Use a liveCD if you have to.

---

### Post by daller on 2005-11-24
[QUOTE=poptones]It contains many files? How is it formatted? ext3?

Is it your goal to test the drive or the file system? does the drive sometimes hang or is the system slow to respond, or did you just start getting errors after a bad shutdown?

To do a basic test just unmount it by doing "sudo su" 

enter fuser -k /dev/{your drive} to make sure there are no open files
umount /dev/{yourdrive} to unmount it
fsck /dev/{yourdrive} to test it. 

If the drive is really new you probably got a bad one and need to perform a more in depth diagnostic. 

first thing is to try backing up your stuff. Use a liveCD if you have to.[/QUOTE]

No important files - at all! (cleaninstall) - Thereby also ext3

...My goal is to test the drive - The filesystem on a cleaninstaller should be O.K. right?

I did this:

fuser -k /dev/hda1 (hda1, right - NOT hda?)
umount /dev/hda1
(busy)

fsck /dev/hda1

..do you really wanna run on mounted filesystem - I answered NO!

I just bumped into this:

typing in "fsck /dev/hda", and pressing TAB, shows me this:
hda hda1 hda2 hda3 hda4 hda5......................hda20

This is not normal, is it?

---

### Post by daller on 2005-11-24
Just started from Dell Diagnostics CD...

Running a HD test now - Seems to take forever! - Goodnight! :D (Not considering your timezone at all - It's midnight here :D)

---

### Post by az on 2005-11-24
On a new drive, I like to to run mke2fs with the -c option twice so that it does a slow read-write (destructive) check.

Example:
sudo mke2fs /dev/hdc1 -c -c -v

---

### Post by daller on 2005-11-24
[QUOTE=azz]On a new drive, I like to to run mke2fs with the -c option twice so that it does a slow read-write (destructive) check.

Example:
sudo mke2fs /dev/hdc1 -c -c -v[/QUOTE]

By "destructive" you mean data destructive? (Since that doesn't matter on an empty disk :))

mke2fs checks the drive, and not just the filesystem?

---

### Post by daller on 2005-11-24
Note: It's not a brand new harddrive - About one year old (has served as my external 2,5" drive)

A lot of people has borrowed it over time, and I'm not sure about it's condition (maybe dropped on the floor, and different other things)

...This is why I'm a little cautious, using it as my primary HD...

I've also started another thread, about buying a really good drive (also bigger) - I'm also running short on space - so buying another drive would have been my christmas present (for myself) anyway...

---

### Post by az on 2005-11-24
[QUOTE=daller]By "destructive" you mean data destructive? (Since that doesn't matter on an empty disk :))

mke2fs checks the drive, and not just the filesystem?[/QUOTE]

Yes, it writes and then reads, so your data is gone.  Mke2fs creates a filesystem, it does not check one like fsck.  If you find some bad secotrs in the middle of your disk, you can always create two different partitions around the bad sectors.

---

### Post by daller on 2005-11-24
[QUOTE=azz]Yes, it writes and then reads, so your data is gone.  Mke2fs creates a filesystem, it does not check one like fsck.  If you find some bad secotrs in the middle of your disk, you can always create two different partitions around the bad sectors.[/QUOTE]

Thank you so much for your help so far!

This seems to take forever :) Goodnight! (Well, I'm probably NOT going to bed! - I'm too excited :D)

How long do you think it'll take?

---

### Post by az on 2005-11-24
[QUOTE=daller]Thank you so much for your help so far!

This seems to take forever :) Goodnight! (Well, I'm probably NOT going to bed! - I'm too excited :D)

How long do you think it'll take?[/QUOTE]
I think I did this on a 40 gig Hdd and it took five hours?  I do not remember.  I went to bed.

I remember I timed it, but I forgot how long it took!

time sudo mke2fs /dev/hdc1 -c -c -v


There probably is a better way to do this, it is just what I did.  I'm just this guy, you know.

---

### Post by voger on 2005-11-26
How can we know if e2fsck finds any bad sectors? It prints a report at the end? Some error message as it goes? If the second then it changes the progress disply line into a new line?

---

