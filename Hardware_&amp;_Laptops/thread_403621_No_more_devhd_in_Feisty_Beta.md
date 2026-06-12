---
title: "No more /dev/hd?? in Feisty Beta?"
date: 2007-04-07
forum: Hardware &amp; Laptops
---

### Post by saltydog on 2007-04-07
I have 2 IDE hard disks and they are listed in /etc/fstab with their own UUID. Until last week, doing a  'sudo fdisk -l' command, it returned the list of partitions in /dev/hda(x) and /dev/hdb(x).

Now, if I make an fdisk list, it returns a list of /dev/sda(x) and /dev/sdb(x).

I do not have sata disks, but EIDE/ATA100. Why I have all /dev/sd??

---

### Post by nashira on 2007-04-07
I noticed the same thing.  At first I thought my 'media' drive had stopped working after an update-initiated reboot, but then I saw that it had just been renamed from hda to sda and my sata drive became sdb.  ...I wonder why...

---

### Post by wonkycross on 2007-04-07
yes, i just recently noticed this too.  though in my /media folder, my partitions are still mounted as hda1, hda2, etc.  also, my dvd-rw drive is detected as scd0.  all my drives, both dvd and hd are ide.  my dvd-drive now mounts as /media/"name of cd/dvd" though.  odd, but everything still works though.

---

### Post by caffienefree on 2007-04-07
[http://www.linuxquestions.org/questions/showthread.php?p=2687180#post2687180](http://www.linuxquestions.org/questions/showthread.php?p=2687180#post2687180)

---

### Post by kakulacis on 2007-04-08
The worst part is - it f*cking changes randomly device id's (actually device/partition names): sda to sdc, sdb to sda and so on. Ok, it was one time till now, but it ain't make me happy to change fstab once per day.

---

### Post by saltydog on 2007-04-08
> **kakulacis said:**
> The worst part is - it f*cking changes randomly device id's (actually device/partition names): sda to sdc, sdb to sda and so on. Ok, it was one time till now, but it ain't make me happy to change fstab once per day.

If you remove from fstab any direct device (/dev/hd?? or /dev/sd??) and use instead the UUIDs, you don't need to change anything.

---

### Post by Najand on 2007-04-08
well.... there is a bug in kernel 2.6.20-11 to 14. It shows all IDE harddisks as SATAs... So you can change all of them to /dev/sd* and it will work for you.
[https://bugs.launchpad.net/ubuntu/+s....20/+bug/82314]("https://bugs.launchpad.net/ubuntu/+s....20/+bug/82314")

---

### Post by kakulacis on 2007-04-08
> **saltydog said:**
> If you remove from fstab any direct device (/dev/hd?? or /dev/sd??) and use instead the UUIDs, you don't need to change anything.

I'm not intended to use some 20 characters id's for my fstab configuration. Yes, uuid's have some pros, but in fact all their proses are opposite with respective cons.

---

### Post by saltydog on 2007-04-09
> **kakulacis said:**
> I'm not intended to use some 20 characters id's for my fstab configuration. Yes, uuid's have some pros, but in fact all their proses are opposite with respective cons.

I don't see the problem..

---

### Post by grim4593 on 2007-04-09
> **saltydog said:**
> I don't see the problem..

UUID's are just strings of seemingly random alphanumerics. When I saw my fstab had been butchered with all these UUID's, I changed them back to something that made sense by restoring my backup.

---

### Post by saltydog on 2007-04-10
> **grim4593 said:**
> UUID's are just strings of seemingly random alphanumerics. When I saw my fstab had been butchered with all these UUID's, I changed them back to something that made sense by restoring my backup.

They are NOT random numbers!
They are your HD's unique identifiers. If you have them in your /etc/fstab, you can move partitions, add hard disks, even move your hard disk from a pc to another, and they will be always identified by the same UUID. Don't care anymore about /dev/hdXX or /dev/sdXX when you move disks or partitions.

---

### Post by saltydog on 2007-04-12
Just one issue: hdparm does not work anymore, now that all disks are /dev/sdXX?

---

### Post by saltydog on 2007-04-16
This morning with -15 kernel everything has turned back! Now I have again my /dev/hdXX discs!!

---

