---
title: "Is it my hard disk?"
date: 2020-09-14
forum: Hardware
---

### Post by janesh25 on 2020-09-14
My laptop decided not to boot up on a normal day.
Instead it showed me a prompt.

Initramfs

I ran 

fsck /dev/sda2

where sda2 holds my ubuntu installation.

It showed some errors and i did yes to all as mentioned on ubuntu forum.
It worked.
But next day again same thing happend.
I did the same thing again and it worked, but this time i decided to take backup of my data to be on the safe side.
Next day again same thing happened and I decided to reinstall ubuntu this time formatting my drive.

Ubuntu woked fine for some hours but later opening of chromium and any application was very slow.

Then it stopped me from writing and copying from my /home folder.
So i decided to format the partition again and reinstall it. I selected the option erase disk and install ubutnu .

After installation starts it shows an error  and cancels the installation of ubuntu in between.

I searched more forums and figured it might have something to do with my hard disk.

So i ran ubuntu live from my usb and ran smart data and self tests.
First time i ran short test.
Overall assessment said -- Disk is ok, 443 bad sectors.

Second time.
Overall assessment said -- Self test failed

And same thing afterwards.

When i take a look at my 1 tb hard disk in disk utility it shows 2 partitions.

Free space 538 mb
Filesystem partition 2 1000 gb ext4

When i try to format partiton 2 it says 

Error unmounting /dev/sda2: target is busy(udisks-erro-quark,14)

What should i do?
What is happening here?

---

### Post by sudodus on 2020-09-14
> **janesh25 said:**
> 
So i ran ubuntu live from my usb and ran smart data and self tests.
First time i ran short test.
Overall assessment said -- Disk is ok, 443 bad sectors.

Second time.
Overall assessment said -- Self test failed

And same thing afterwards.


I think that your HDD is demaged beyond repair. I'm glad that you managed to get a fresh backup before it was too late.

You need a new drive. 

If the backup is a disk image: Get a drive with at least the same size (not one single byte smaller) and restore from the backup to this new drive.

If the backup is on the file level: Get a drive size that you want now (smaller or bigger). Reinstall or maybe install a newer version of Ubuntu. Restore the data files from your backup.

---

### Post by janesh25 on 2020-09-14
Thanks for the help @sudodus.

Planning to replace it with a SSD now.
My backup is at a file level in an external HDD.

I cant seem to understand one thing though.

When i took the backup.I almost copied 700 GB of data. Took me many hours.
My hard disk went through all that without complaining.
Is it that some partition is working fine and some not ?
Or is it something else with the hard drive ?

---

### Post by sudodus on 2020-09-14
There may be some particular physical locations of the drive that are bad, and you were reading from good locations. Or maybe the problems will show up when writing, and the big backup was a reading process. Or you were lucky during the backup.

---

### Post by janesh25 on 2020-09-14
Ok.
I'll get that new SSD now.

Thank you.

---

### Post by TheFu on 2020-09-14
I consider 1 bad sector to be a problem and order a replacement drve when that happens.
443 bad sectors s a level tat I consider the building, apartments, and 20 families at risk of death over.  If you install smartctl on the new install and setup alarms, you'll get notified when there are and smart problems on any connected storage.  Waiting until something bad happens laves it to chance where the bad sectors are located.  

You were lucky this time.  Very lucky. I've had storage just stop working without any notice.  A buddy reported yesterday that his 3 month old SSD died last week. It was a name brand, well liked model.  We just never know.  Be certain you have backups to match how important any data may be.

---

