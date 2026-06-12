---
title: "System Imaging"
date: 2008-08-26
forum: General Help
---

### Post by vjkeito on 2008-08-26
Hi I have recently setup a fresh system with 4 partitions

partition #1 = swap (1.5gb)
**partition #2 = /    (15gb)**
partition #3 = /home (400gb)
**[COLOR="Red"]partition #4 = system backup image (15gb)[/COLOR]**

what I need to know is...

to copy this system (part#2) exactly as it is, so if needs be after a complete system meltdown, I can just restore from part#4 what method should I use?

I have booted gparted live and that gives the option to copy a partition to another.  I did this and it appeared to copy the system, but does it copy everything needed?  from what info I can gather from almost all tutorials on the subject this method is never pointed out, instead it seems most would recommend booting into clonezilla after partitioning with gparted.

I've just reformatted part#4 (reiserfs, the same as part#2) and now I want to know, should I copy and paste the partition with gparted, or should I clone the partition to an image with clonezilla?

Some feedback on exactly why 1 is preferred over the other would be much appreciated.

regards
keito

---

### Post by vjkeito on 2008-08-27
wow! not 1 reply, that's a first.

FYI - I used clonezilla, I noted it takes a copy of the MBR (something I'm not so sure of with gparted) and can compress the image too which is also a benefit.

---

### Post by mellowd on 2008-08-27
If it's an entire backup of just one partition, you could use tar as well. Tar will back up every single file and that's all that's needed

---

### Post by robert shearer on 2008-08-27
Another back-up option is to make a live cd/dvd of your current running system. this would include all your apps, data and configuration/setup files.
If you crash your system then you can use your custom cd/dvd to quickly re-install your customised o/s.
These links explain it more fully,,

[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

I make a monthly remaster back-up and it works without trouble on my old celeron 1Ghz/512Mb ram/ 16Mb video card so should work on most anything else.

---

### Post by kpkeerthi on 2008-08-27
I prefer to use least intrusive methods using tar or rsync or rsnapshot so automating them (using a cron) is easy.

clonezilla/gparted requires you to start the process 'manually' and there is no way to automate.

---

### Post by vjkeito on 2008-08-27
I've had a look into a time-machine type backup utility - flyback, timevault, sbackup amongst others.

problem is flyback looked like the most promising but development seems to have stopped.

what partitcular "user-friendly" packages are there still under heavy development that would fit the bill?

[QUOTE="robert shearer"]
Another back-up option is to make a live cd/dvd of your current running system. this would include all your apps, data and configuration/setup files.
If you crash your system then you can use your custom cd/dvd to quickly re-install your customised o/s.
These links explain it more fully,,
[/QUOTE]

I have looked into this before and it could be a viable solution, but what if your system is larger than 8gb?

---

### Post by robert shearer on 2008-08-27
8Gb?? not sure of your concern. Do you mean the size of a dvd backup limited to 8Gb?.

Remastersys uses a compressed filesystem as used on the Ubuntu install disk so, presumably, uncompresses on the fly.
I have yet to try by including a huge amount of personal data (easier to copy this to and external hard drive and then backup the o/s using remastersys)
Might be something to check on the Remastersys forum..

[http://loscompanion.com/forums/index.php?board=58.0](http://loscompanion.com/forums/index.php?board=58.0)


Just checked,
Looks like the limit is a compressed file of 4Gb as per this link..

[http://loscompanion.com/forums/index.php?topic=4249.0](http://loscompanion.com/forums/index.php?topic=4249.0)

---

