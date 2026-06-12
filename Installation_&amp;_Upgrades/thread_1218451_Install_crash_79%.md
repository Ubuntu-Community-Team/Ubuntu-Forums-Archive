---
title: "Install crash 79%"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by UbuntuniX on 2009-07-20
I'm installing Ubuntu 9.04 with /home on a separate partition. When the installer gets to 79%, "creating user", ubiquity just crashes. :confused:

---

### Post by UbuntuniX on 2009-07-20
I successfully installed on a separate, empty partition and can still access files on my old home partition, but this is quite an annoyance.

---

### Post by Bartender on 2009-07-20
I wonder if the drive is damaged?  Maybe try what they suggest in this thread
[http://ubuntuforums.org/showthread.php?t=1218063](http://ubuntuforums.org/showthread.php?t=1218063)

---

### Post by UbuntuniX on 2009-07-20
> **Bartender said:**
> I wonder if the drive is damaged?  Maybe try what they suggest in this thread
[http://ubuntuforums.org/showthread.php?t=1218063](http://ubuntuforums.org/showthread.php?t=1218063)

I don't think it is; all my files are still intact. I ran badblocks and it didn't return any results.

---

### Post by UbuntuniX on 2009-07-24
Still an issue. :(

---

### Post by UbuntuniX on 2009-07-25
After having Debian installed briefly, I was able to install Ubuntu with no problems. Maybe a bug with formatting partitions?

---

### Post by lukjad on 2009-07-25
It's possible. It could also just be some random bug.

---

### Post by markbuntu on 2009-07-25
Did a bug report get generated?

If you have some other distros on the machine then ubiquity will crash trying to migrate your settings etc. You can try this, which is what I had to do.
Run the live cd and open a terminal and type

ubiquity --no-migration-assistant

The installer will run as usual but will not try to migrate anything.

---

### Post by UbuntuniX on 2009-07-26
> **markbuntu said:**
> Did a bug report get generated?

If you have some other distros on the machine then ubiquity will crash trying to migrate your settings etc. You can try this, which is what I had to do.
Run the live cd and open a terminal and type

ubiquity --no-migration-assistant

The installer will run as usual but will not try to migrate anything.

No report, unfortunately. I don't know about migration because my old home directory had *all* settings and such deleted, just leaving music and documents and all that.

---

### Post by pacofvf on 2009-11-18
I'm installing 9.04 in a toshiba with an old Ati graphics card, because 9.10 is a pain in the @$$, I have the same problem here, any news about this issue?

---

### Post by UbuntuniX on 2009-11-19
> **pacofvf said:**
> I'm installing 9.04 in a toshiba with an old Ati graphics card, because 9.10 is a pain in the @$$, I have the same problem here, any news about this issue?

It seems to be a problem with gparted in Ubuntu; I installed Debian, wiping the partition, and was able to install Ubuntu after that.

---

